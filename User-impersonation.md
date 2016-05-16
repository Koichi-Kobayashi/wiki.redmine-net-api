####User impersonation

As of Redmine 2.2.0 you can impersonate user setting user login (eg. jsmith). 

- This only works when using the API with an **administrator account**
- This header will be ignored when using the API with a regular user account.

**Example:**

```
var host = "<host>";
var apiKey = "<api-key>";
var login = "<user-login-to-impersonate>";

RedmineManager manager = new RedmineManager (host, apiKey);
manager.ImpersonateUser = login;
```