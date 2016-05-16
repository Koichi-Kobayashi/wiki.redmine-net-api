#### Delete wiki page

Deletes a wiki page, its attachments and its history. If the deleted page is a parent page, its child pages are not deleted but changed as root pages.

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
            string projectId = "<project-id>";
            string wikiPageName = "<wiki-page-Name>";
            var manager = new RedmineManager(host, apiKey);

            try
            {
               manager.DeleteWikiPage(projectId, wikiPageName);
            }
            catch(NotFoundException nfe)
            {
              Console.WriteLine("WikiPage not found.");
              return;
            }
            catch(RedmineException rex)
            {
              Console.WriteLine("Delete WikiPage returned exception {0}.", rex.Message);
              return;
            }

            try
            { 
              manager.GetWikiPage(projectId, null, wikiPageName)
            }
            catch(NotFoundException nfe)
            {
              Console.WriteLine("WikiPage deleted successfully.");
              return;
            }
            catch(RedmineException rex)
            {
              Console.WriteLine("Get WikiPage returned error {0}.", rex.Message);
              return;
            }
            Console.WriteLine("WikiPage was not deleted.");
        }
    }
}
```

**Async Example:**
```
...
  await manager.DeleteWikiPageAsync(projectId, wikiPageName);
...
```