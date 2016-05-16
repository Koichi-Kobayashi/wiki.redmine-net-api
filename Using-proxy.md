####Using proxy

RedmineManager handles proxy servers.

**Example:**

```
var host = "<host>";
var apiKey = "<api-key>";
IWebProxy webProxy = WebRequest.GetSystemWebProxy();

RedmineManager manager = new RedmineManager(host, apiKey, webProxy);
```