#### Remove user from group

Removes a user from a group.

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
               int userId = <user-id-to-be-removed>;
               manager.RemoveUserFromGroup(groupId, userId);

               var group = manager.GetObject<Group>(groupId, 
                                     new NameValueCollection() { { RedmineKeys.INCLUDE, RedmineKeys.USERS } });

               Console.WriteLine("Group without the removed user: {0}.", group);
           }
        }
    }
```