#### Add user to group

Adds an existing user to a group.

**Parameters:**

`user_id` (required): id of the user to add to the group.

**Sync Example:**

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

           var group = manager.GetObject<Group>(groupId, 
                                new NameValueCollection() { { RedmineKeys.INCLUDE, RedmineKeys.USERS } });

           Console.WriteLine("Group with added user: {0}.", group);
        }
    }
}
```

**Async Example:**

```
...
  await manager.AddUserToGroupAsync(groupId, userId);
...
```