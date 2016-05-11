Returns a paginated list of type T.

The default page size is 25. The default maximum page size is 100.

Parameters:

* offset: skip this number of issues in response (optional)
* limit: number of issues per page (optional)
* sort: column to sort with. Append :desc to invert the order.

Optional filters: (Issue)

* project_id: get issues from the project with the given id, where the id is either project id or project identifier
* subproject_id: get issues from the subproject with the given id. You can use project_id=XXX&subproject_id=!* to get only the issues of a given project and none of its sub projects.
* tracker_id: get issues from the tracker with the given id
* status_id: get issues with the given status id only. Possible values: open, closed, * to get open and closed issues, status id
* assigned_to_id: get issues which are assigned to the given user id. **me** can be used instead an ID to fetch all issues from the logged in user (via API key or HTTP auth)
* cf_x: get issues with the given value for custom field with an ID of x. (Custom field must have 'used as a filter' checked.)
* created_on: fetch issues for a date range.

Example:

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

               //parameter - get paginated list of issues
               var parameters = new NameValueCollection {{RedmineKeys.STATUS_ID, RedmineKeys.ALL}, 
                                          { RedmineKeys.OFFSET, "2" }, 
                                          { RedmineKeys.LIMIT, "5" }, 
                                          { RedmineKeys.SORT, "id:desc" }};

               //parameter - fetch issues for a date range
               parameters.Add(RedmineKeys.CREATED_ON, "><2012-03-01|2012-03-07");

               foreach (var issue in manager.GetPaginatedObjects<Issue>(parameters))
               {
                   Console.WriteLine("#{0}: {1}", issue.Id, issue.Subject);
               }
            }
         }
     }
