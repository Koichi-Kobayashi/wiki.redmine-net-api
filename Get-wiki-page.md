#### Get wiki page

Returns the details of a wiki page.

**Includable:**
  - attachments

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
               manager.GetWikiPage(projectId, 
                                  new NameValueCollection { { RedmineKeys.INCLUDE, RedmineKeys.ATTACHMENTS } }, 
                                  wikiPageName);
           }
        }
    }

#### Getting an old version of a wiki page

Returns the details of an old version of a wiki page.

**Includable:**
  - attachments

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
               int wikiPageVersion = <wiki-page-old-version>;
               manager.GetWikiPage(projectId, 
                                  new NameValueCollection { { RedmineKeys.INCLUDE, RedmineKeys.ATTACHMENTS } }, 
                                  wikiPageName,
                                  wikiPageVersion);
           }
        }
    }