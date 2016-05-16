#### Get current user

Returns the details about the user whose credentials are used to access the API.

**Example:**

```
    using System;
    using Redmine.Net.Api;
    using Redmine.Net.Api.Types;

    namespace RedmineTest
    {
        class Program
        {
            static void Main(string[] args)
            {
               string host = "<host>";
               string apiKey = "<api-key>";

               var manager = new RedmineManager(host, apiKey);

               User currentUser = manager.GetCurrentUser();

               Console.WriteLine("Current user: {0}.", currentUser);
           }
        }
    }
```