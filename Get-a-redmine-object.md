#### Getting an object of type T. ####

**Parameters: (Issue)**

> include: fetch associated data (optional).

> Possible values: children, attachments, relations, changesets and journals.

To fetch multiple associations use comma (e.g ?include=relations,journals).

**Example:**
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
            Console.WriteLine("#{0}: {1}", issue.Id, issue.Subject);
        }
    }
}
```