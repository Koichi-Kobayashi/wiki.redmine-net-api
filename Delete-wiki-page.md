#### Delete wiki page

Deletes a wiki page, its attachments and its history. If the deleted page is a parent page, its child pages are not deleted but changed as root pages.

** Example: **

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
            string projectId = "<project-id>";
            string wikiPageName = "<wiki-page-Name>";
            var manager = new RedmineManager(host, apiKey);

            manager.DeleteWikiPage(projectId, wikiPageName);
        }
    }
}
```