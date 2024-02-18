---
title: 'Deploying a Machine Learning Model as an API with FastAPI, Docker, and Knative'
date: 2024-02-16 17:26:08
tags: ["machine learning", "API development", "FastAPI", "Docker", "Knative", "model deployment", "serverless scaling"]
---

In the post {% post_link Classification-with-scikit-learn Leveraging scikit-learn for Invoice Classification using Text Data %}, we explored how to train a machine learning model to classify invoices based on their textual content using scikit-learn. However, once we have a model trained, a natural next step is to make it accessible to other systems or services through an API. This raises the question: how do we deploy it as a scalable API?

In this blog post, we'll address this question by walking through the process of wrapping our scikit-learn model as an API using FastAPI, containerizing it with Docker, and deploying it on Knative for serverless scaling. Let's dive in!

## Wrapping the Model as an API with FastAPI

We'll start by wrapping our machine learning model as an API using FastAPI, a modern web framework for building APIs with Python. FastAPI offers automatic OpenAPI documentation generation and high performance, making it an excellent choice for our use case.

```python
import pickle
from typing import Dict, List
from fastapi import FastAPI
from pydantic import BaseModel, Field
from util.get_prediction_probabilities import get_prediction_probabilities

def load_model():
    with open("model.pkl", "rb") as file:
        model = pickle.load(file)
    return model

model = load_model()
app = FastAPI()

class PredictionResult(BaseModel):
    text: str
    prediction: str
    probabilities: Dict[str, float]

class PredictionResponse(BaseModel):
    results: List[PredictionResult] = Field(
        examples=[
            {
                "text": "netflix訂閱",
                "prediction": "subscription",
                "probabilities": {
                    "subscription": 0.916624393150892,
                    "learning": 0.023890389044000114,
                },
            },
        ]
    )

class PredictionRequest(BaseModel):
    texts: List[str] = Field(..., example=["netflix訂閱"])

@app.post("/predict", response_model=PredictionResponse)
async def predict(request: PredictionRequest):
    texts = request.texts
    results = get_prediction_probabilities(model, texts)
    return {"results": results}
```

## Building a Docker Image

Next, we'll containerize our FastAPI application using Docker. Docker provides a lightweight and portable way to package applications and their dependencies into containers, ensuring consistency across different environments.

```Dockerfile
# Use a base image with Python installed
FROM python:3.9-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt .

# Install the Python dependencies
RUN pip install -r requirements.txt

# Copy the application code
COPY . .

# Set the entrypoint command
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "5050"]
```

## Deployment on Knative

Finally, we'll deploy our Docker image to Knative, a Kubernetes-based platform for building, deploying, and managing modern serverless workloads. Knative offers auto-scaling capabilities, allowing our API to handle varying levels of traffic efficiently.

```yaml
apiVersion: serving.knative.dev/v1
kind: Service
metadata:
  name: invoice-classifier
spec:
  template:
    metadata:
      annotations:
        autoscaling.knative.dev/target-burst-capacity: "500"
        autoscaling.knative.dev/class: "hpa.autoscaling.knative.dev"
        autoscaling.knative.dev/metric: "cpu"
        autoscaling.knative.dev/target: "60"
        autoscaling.knative.dev/minScale: "2"
    spec:
      containers:
      - name: invoice-classifier
        image: your-docker-registry/invoice-classifier
        resources:
          limits:
            cpu: 1
            memory: 2Gi
          requests:
            cpu: 300m
            memory: 500Mi
```

## Conclusion

In this blog post, we've demonstrated how to deploy a machine learning model as an API using FastAPI, Docker, and Knative. By following these steps, you can make your machine learning models accessible as scalable and reliable APIs, enabling seamless integration into your applications and workflows.
