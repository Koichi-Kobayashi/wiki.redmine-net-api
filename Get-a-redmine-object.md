#### Getting an object of type T. ####

**Parameters: (Issue)**

> include: fetch associated data (optional).

> Possible values: children, attachments, relations, changesets and journals.

To fetch multiple associations use comma (e.g ?include=relations,journals).

**Sync Example (Issue):**
```
using System;
using System.Collections.Specialized;
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
            string issueId = "<issue-id>";
            var manager = new RedmineManager(host, apiKey);

            //parameter - fetch associated relations.
            var parameters = new NameValueCollection {{RedmineKeys.INCLUDE, RedmineKeys.RELATIONS}};
      
            var issue = manager.GetObject<Issue>(issueId, parameters);
            Console.WriteLine("Issue: {0}.", issue);
        }
    }
}
```

**Async Example (Issue):**
```
using System;
using System.Collections.Specialized;
using Redmine.Net.Api;
using Redmine.Net.Api.Types;
using Redmine.Net.Api.Async;
using System.Threading.Tasks;

namespace RedmineTest
{
    class Program
    {  
        static RedmineManager manager;
        static void Main(string[] args)
        {
            string host = "<host>";
            string apiKey = "<api-key>";

            manager = new RedmineManager(host, apiKey);

            var issue = GetObject().Result;
            Console.WriteLine("Issue: {0}.", issue);
        }

        public static async Task<Issue> GetObject()
        {
            string issueId = "<issue-id>";
            
            var parameters = new NameValueCollection {{RedmineKeys.INCLUDE, RedmineKeys.RELATIONS}};
      
            var issue = await manager.GetObjectAsync<Issue>(issueId, parameters);
            return issue;
        }
    }
}
```