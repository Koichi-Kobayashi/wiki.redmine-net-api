##### Create or update wiki page

Creates or updates a wiki page.

When updating an existing page, you can include a version attribute to make sure that the page is a specific version when you try to update it (eg. you don't want to overwrite an update that would have been done after you retrieved the page).

**Example:**

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

               string projectId = "<project-id>";
               string wikiPageName = "<wiki-page-name>";
               WikiPage page = manager.CreateOrUpdateWikiPage(projectId, 
                                 wikiPageName, 
                                 new WikiPage 
                                     { 
                                       Text = "<wiki-page-text>", 
                                       Comments = "<wiki-page-comment>", 
                                       Version = <wiki-page-version> 
                                     }
                                 );
           }
        }
    }