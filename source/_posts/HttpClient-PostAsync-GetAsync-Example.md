---
title: HttpClient PostAsync/GetAsync JSON Example
date: 2018-04-11 18:52:32
tags: [HttpClient, .NET, GetAsync, PostAsync, C#]
---

## PostAsync

```csharp
static readonly HttpClient Client = new HttpClient();
public async Task<T> PostAsync<T>(string url, T data) where T : class, new()
{
    try
    {
        string content = JsonConvert.SerializeObject(data);
        var buffer = Encoding.UTF8.GetBytes(content);
        var byteContent = new ByteArrayContent(buffer);
        byteContent.Headers.ContentType = new MediaTypeHeaderValue("application/json");
        var response = await Client.PostAsync(url, byteContent);
        string result = await response.Content.ReadAsStringAsync();
        if (response.StatusCode != HttpStatusCode.OK)
        {
            logger.Error($"GetAsync End, url:{url}, HttpStatusCode:{response.StatusCode}, result:{result}");
            return new T();
        }
        logger.Info($"GetAsync End, url:{url}, result:{result}");
        return JsonConvert.DeserializeObject<T>(result);
    }
    catch (WebException ex)
    {
        if (ex.Response != null)
        {
            string responseContent = new StreamReader(ex.Response.GetResponseStream()).ReadToEnd();
            throw new System.Exception($"response :{responseContent}", ex);
        }
        throw;
    }
}
```

## GetAsync

```csharp
static readonly HttpClient Client = new HttpClient();
public static async Task<T> GetAsync<T>(string url, int timeout = 10000) where T : class, new()
{
    try
    {
        Logger.Debug($"GetAsync Start, url:{url}, timeout:{timeout}");
        var response = await Client.GetAsync(url).ConfigureAwait(false);
        string result = await response.Content.ReadAsStringAsync();
        if (response.StatusCode != HttpStatusCode.OK)
        {
            Logger.Error($"GetAsync End, url:{url}, HttpStatusCode:{response.StatusCode}, result:{result}");
            return new T();
        }
        Logger.Debug($"GetAsync End, url:{url}, result:{result}");
        return JsonConvert.DeserializeObject<T>(result);
    }
    catch (WebException ex)
    {
        if (ex.Response != null)
        {
            string responseContent = new StreamReader(ex.Response.GetResponseStream()).ReadToEnd();
            throw new System.Exception($"response :{responseContent}", ex);
        }
        throw;
    }
}
```