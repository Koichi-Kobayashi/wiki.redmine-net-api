#### Get a redmine object list

Returns list with all objects of type T.

**Parameters:**

* `sort`: column to sort with. Append `:desc` to invert the order.

**Optional filters: (Issue)**

* `project_id`: get issues from the project with the given id, where the id is either project id or project identifier
* `subproject_id`: get issues from the subproject with the given id. You can use `project_id=XXX&subproject_id=!*` to get only the issues of a given project and none of its sub projects.
* `tracker_id`: get issues from the tracker with the given id
* `status_id`: get issues with the given status id only. Possible values: __open, closed, *__ to get open and closed issues, status id
* `assigned_to_id`: get issues which are assigned to the given user id. **me** can be used instead an ID to fetch all issues from the logged in user (via API key or HTTP auth)
* `cf_x`: get issues with the given value for custom field with an ID of x. (Custom field must have 'used as a filter' checked.)
* `created_on`: fetch issues for a date range.

**Sync Example:**

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
           var manager = new RedmineManager(host, apiKey);

           //parameter - get all issues
           var parameters = new NameValueCollection {{RedmineKeys.STATUS_ID, RedmineKeys.ALL}};

           //parameter - fetch issues for a date range
           parameters.Add(RedmineKeys.CREATED_ON, "><2012-03-01|2012-03-07");

           foreach (var issue in manager.GetObjects<Issue>(parameters))
           {
               Console.WriteLine("Issue: {0}.", issue);
           }
        }
     }
 }
```

**Async Example:**

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

           foreach (var issue in GetIssues().Result)
           {
               Console.WriteLine("Issue: {0}.", issue);
           }
        }

        public static async Task<List<Issue>> GetIssues()
        {
           //parameter - get all issues
           var parameters = new NameValueCollection {{RedmineKeys.STATUS_ID, RedmineKeys.ALL}};

           //parameter - fetch issues for a date range
           parameters.Add(RedmineKeys.CREATED_ON, "><2012-03-01|2012-03-07");

           return await manager.GetObjectsAsync<Issue>(parameters);
        }
     }
 }
```
