---
title: HttpClient PostAsync/GetAsync JSON Example
date: 2018-04-11 18:52:32
tags: [HttpClient, .NET, GetAsync, PostAsync, C#]
---

## PostAsync

```csharp
static readonly HttpClient Client = new HttpClient();
public async Task<T> PostAsync<T>(string url, object data) where T : class, new()
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
public async Task<string> GetAsync(string url, object data)
{
    try
    {
        string requestUrl = $"{url}?{GetQueryString(data)}";
        logger.Info($"GetAsync Start, requestUrl:{requestUrl}");
        var response = await Client.GetAsync(requestUrl).ConfigureAwait(false);
        string result = await response.Content.ReadAsStringAsync();
        logger.Info($"GetAsync End, requestUrl:{requestUrl}, HttpStatusCode:{response.StatusCode}, result:{result}");
        return result;
    }
    catch (WebException ex)
    {
        if (ex.Response != null)
        {
            string responseContent = new StreamReader(ex.Response.GetResponseStream()).ReadToEnd();
            throw new Exception($"Response :{responseContent}", ex);
        }
        throw;
    }
}

private static string GetQueryString(object obj)
{
    var properties = from p in obj.GetType().GetProperties()
                        where p.GetValue(obj, null) != null
                        select p.Name + "=" + HttpUtility.UrlEncode(p.GetValue(obj, null).ToString());

    return String.Join("&", properties.ToArray());
}
```