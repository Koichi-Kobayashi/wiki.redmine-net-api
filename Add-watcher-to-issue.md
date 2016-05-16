#### Add a watcher to issue

Option available for Redmine 2.3.0 and higher.

**Parameters:**
 - `user_id` (required): id of the user to add as a watcher

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

               int watcherIssueId = <watcher-issue-id>;
               int watcherUserId = <watcher-user-id>;

               manager.AddWatcherToIssue(watcherIssueId, watcherUserId);

               Issue issue = manager.GetObject<Issue>(watcherIssueId.ToString(), 
                                    new NameValueCollection { { RedmineKeys.INCLUDE, RedmineKeys.WATCHERS } });

               Console.WriteLine("Issue with watcher: {0}.", issue);
           }
        }
    }
```