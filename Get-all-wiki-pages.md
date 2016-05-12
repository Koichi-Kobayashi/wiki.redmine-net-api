#### Get all wiki pages

Returns the list of all pages in a project wiki.

**Example:**

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

               string projectId = "<project-id>";
               List<WikiPage> pages = (List<WikiPage>)manager.GetAllWikiPages(projectId);


            }
         }
     }