---
title: Training a Model to Solve CAPTCHA Audio Challenges
date: 2023-07-02 20:55:11
tags: [CAPTCHA, Machine Learning, SVM, Audio Processing, Feature Extraction, Automation, User Experience, Web Security, Data Science, Python Programming]
---

In this blog post, we will explore how to train a machine learning model to solve CAPTCHA audio challenges. CAPTCHA is a widely used security measure on the web to prevent automated bots from accessing websites. It presents users with various tests to determine if they are human, one of which is the audio challenge. By training a model to solve these audio challenges, we can automate the process and improve user experience. Let's dive into the code and understand how it works.

## The Setup

Before we get into the code, let's understand the directory structure and dependencies required for this project. Here's an overview:

1. `login-captcha-example`: This directory contains the audio files used for training and testing the model.
2. `material`: This directory contains the labeled training audio files. Each audio file represents a digit in the captcha.
3. `svm_model.pkl`: This is the trained SVM model file that will be generated during training.
4. `temp`: This directory will be used to store temporary audio files generated during the prediction process.

To get started, make sure you have the following dependencies installed:
- `os`: A module for interacting with the operating system.
- `librosa`: A library for audio and music signal analysis.
- `numpy`: A library for mathematical operations on multi-dimensional arrays.
- `sklearn.svm`: The SVM (Support Vector Machine) model implementation from scikit-learn.
- `sklearn.metrics`: A module for evaluating the performance of machine learning models.
- `subprocess`: A module for spawning new processes and executing system commands.
- `string.Template`: A class for string templating.
- `joblib`: A library for serializing Python objects to disk and loading them back into memory.

## Code Walkthrough
<!-- more -->

Let's go through the code step by step to understand how the model is trained and used for predictions.

### Training the Model

The `train_model` function is responsible for training the SVM model using the provided audio data. Here's how it works:

```python
def train_model():
  X = []
  y = []
  for file in os.listdir(train_material_dir):
      if file.endswith('.wav'):
          file_path = os.path.join(train_material_dir, file)
          label = file.split('.')[0]  # Extract the label from the file name
          y.extend(list(label))  # Extend the label list for each digit
          feature = extract_features(file_path)
          X.append(feature)

  # Training the SVM model
  svm = SVC(kernel='rbf')
  svm.fit(X, y)

  # Model evaluation
  y_pred = svm.predict(X)
  accuracy = accuracy_score(y, y_pred)
  print("Accuracy:", accuracy)
  dump_model(svm)
```

First, it iterates over the audio files in the `train_material_dir` directory and extracts the labels (digits) from the file names. The features (MFCC coefficients) are then extracted using the `extract_features` function. The labels and features are stored in separate lists.

Next, an SVM model is instantiated with the 'rbf' (Radial Basis Function) kernel and trained on the extracted features and labels. The accuracy of the trained model is evaluated using the `accuracy_score` function.

Finally, the trained model is serialized using the `joblib` library and saved to the `svm_model.pkl` file using the `dump_model` function.

### Preparing Audio Files for Prediction

Before making predictions, the `split_by_silence` function splits the input audio file into smaller chunks based on silence. This is necessary because the audio files used for training and testing may have silence between digits. Here's how it works

:

```python
def split_by_silence(file_path):
  os.makedirs(temp_dir, exist_ok=True)
  sox_template = Template('sox "${src}" "${dst}" silence 1 0.02 1% 1 0.02 1% : newfile : restart')
  sox_cmd = sox_template.substitute(src=file_path, dst=f'temp/%n.wav')
  subprocess.run(sox_cmd, shell=True)
```

The function creates the `temp` directory if it doesn't already exist. It then uses the `sox` command-line tool to split the audio file based on silence, generating separate audio files for each chunk.

### Extracting Features

The `extract_features` function extracts the Mel-Frequency Cepstral Coefficients (MFCCs) from an audio file. Here's how it works:

```python
def extract_features(file_path):
  audio, sr = librosa.load(file_path)
  # By using MFCC to extract features, the item in the audio could reduce from 5000+ to 20*30 2D array
  mfcc = librosa.feature.mfcc(y=audio, sr=sr)
  # By np.mean, it could reduce from 20*30 2D array to 20 in 1D array, which could be used as the input of SVM
  mfcc_mean = np.mean(mfcc, axis=1)  # Take the mean across MFCC coefficients
  return mfcc_mean
```

Using the `librosa` library, the function loads the audio file and computes the MFCCs. The resulting MFCC matrix is then reduced to a 1D array by taking the mean along the second axis. This reduced feature vector is suitable for inputting into the SVM model.

### Making Predictions

The `predict` function uses the trained SVM model to predict the digits present in the input audio file. Here's how it works:

```python
def predict(file_path):
  split_by_silence(file_path)
  loaded_model = joblib.load(model_file)
  result = ''
  # only 5 digits in the audio file, but SOX splits it by silence into 6 files
  for i in range(1, 6):
    filename = f"{str(i).zfill(2)}.wav"
    chunk_file_path = os.path.join(temp_dir, filename)
    X = extract_features(chunk_file_path)
    result += loaded_model.predict([X])[0]

  return result
```

First, the `split_by_silence` function is called to split the input audio file into smaller chunks. The trained SVM model is then loaded from the `svm_model.pkl` file.

Next, the function iterates over the chunked audio files, extracts features using the `extract_features` function, and predicts the digit using the loaded model. The predicted digits are concatenated to form the final result.

Finally, the predicted result is returned by the function.

### Putting It All Together

The code concludes by training the model using the `train_model` function and making predictions for each audio file in the `data_dir` directory:

```python
train_model()
for file in os.listdir(data_dir):
  result = predict(os.path.join(data_dir, file))
  print(result, file)
```

The `train_model` function is called to train the model on the provided training data. Then, for each audio file in the `data_dir` directory, the `predict` function is called to generate the predicted result. The result is printed along with the file name.

## Conclusion

In this blog post, we explored how to train a machine learning model to solve CAPTCHA audio challenges

. By using the SVM model and extracting MFCC features from the audio, we were able to achieve accurate predictions. This approach can be further improved and extended to handle more complex audio challenges. By automating the resolution of audio captchas, we can enhance user experience and streamline website access. Feel free to experiment with the code and adapt it to your specific needs.

## Source code

https://github.com/Asing1001/audio-captcha-svm
