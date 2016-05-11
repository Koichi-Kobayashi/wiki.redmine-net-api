Returns list with all objects of type T.

Parameters:

* sort: column to sort with. Append :desc to invert the order.

Optional filters: (Issue)

* project_id: get issues from the project with the given id, where the id is either project id or project identifier
* subproject_id: get issues from the subproject with the given id. You can use project_id=XXX&subproject_id=!* to get only the issues of a given project and none of its sub projects.
* tracker_id: get issues from the tracker with the given id
* status_id: get issues with the given status id only. Possible values: open, closed, * to get open and closed issues, status id
* assigned_to_id: get issues which are assigned to the given user id. **me** can be used instead an ID to fetch all issues from the logged in user (via API key or HTTP auth)
* cf_x: get issues with the given value for custom field with an ID of x. (Custom field must have 'used as a filter' checked.)
* created_on: fetch issues for a date range.

Obs: operators containing ">", "<" or "=" should be hex-encoded so they're parsed correctly. 

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
               string host = "";
               string apiKey = "";
               var manager = new RedmineManager(host, apiKey);

               //parameter - get all issues
               var parameters = new NameValueCollection {{"status_id", "*"}};

               //parameter - fetch issues for a date range
               parameters.Add("created_on", "><2012-03-01|2012-03-07");

               foreach (var issue in manager.GetObjects<Issue>(parameters))
               {
                   Console.WriteLine("#{0}: {1}", issue.Id, issue.Subject);
               }
            }
         }
     }

Getting the total issues that are available

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
                string host = "";
                string apiKey = "";

                var manager = new RedmineManager(host, apiKey);

                //parameter - get all issues
                var parameters = new NameValueCollection {{"status_id", "*"}};
                int totalItems;
                var items = manager.GetObjects<Issue>(parameters, out totalItems);

                Console.WriteLine("Total items: {0}", totalItems);
                foreach (var issue in )
                {
                    Console.WriteLine("#{0}: {1}", issue.Id, issue.Subject);
                }
            }
        }
    }

Getting all the issues that are available:

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
                string host = "";
                string apiKey = "";

                var manager = new RedmineManager(host, apiKey);

                //parameter - get all issues
                var parameters = new NameValueCollection {{"status_id", "*"}};

                foreach (var issue in manager.GetObjects<Issue>(parameters))
                {
                    Console.WriteLine("#{0}: {1}", issue.Id, issue.Subject);
                }
            }
        }
    }