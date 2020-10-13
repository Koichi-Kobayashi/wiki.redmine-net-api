#### Authentication

The authentication can be done in 2 different ways:

- HTTP Basic authentication

**Example:**

```
var host = "<host>";
var login = "<login>";
var password = "<password>";
RedmineManager manager = new RedmineManager(host, login, password);
```

- ApiKey

  To enable the API-style authentication, you have to check Enable REST API in Administration -> Settings ->  Authentication.
  
  You can find your API key on your account page ( /my/account ) when logged in, on the right-hand pane of the default layout.

**Example:**

```
var host = "<host>";
var apiKey = "<api-key>";
RedmineManager manager = new RedmineManager(host, apiKey);
```