#### Add user to group

Adds an existing user to a group.

**Parameters:**

`user_id` (required): id of the user to add to the group.

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

               int groupId = <group-id>;
               int userId = <user-id-to-be-added>;
               manager.AddUserToGroup(groupId, userId);
           }
        }
    }
```