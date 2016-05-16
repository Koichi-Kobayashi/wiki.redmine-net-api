#### Get wiki page

Returns the details of a wiki page.

**Includable:**
  - attachments

**Sync Example:**

```
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
           WikiPage page = manager.GetWikiPage(projectId, 
                                  new NameValueCollection { { RedmineKeys.INCLUDE, RedmineKeys.ATTACHMENTS } }, 
                                  wikiPageName);

           Console.WriteLine("WikPage details: {0}.", page);
         }
    }
}
```

#### Getting an old version of a wiki page

Returns the details of an old version of a wiki page.

**Includable:**
  - attachments

**Sync Example:**

```
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
           WikiPage page = manager.GetWikiPage(projectId, 
                                  new NameValueCollection { { RedmineKeys.INCLUDE, RedmineKeys.ATTACHMENTS } }, 
                                  wikiPageName,
                                  wikiPageVersion);

           Console.WriteLine("WikPage details: {0}.", page);
        }
    }
}
```

**Async Example:**
```
...
  await manager.GetWikiPageAsync(projectId, 
                                 new NameValueCollection { { "include", "attachments" } }, 
                                 wikiPageName);
...
```