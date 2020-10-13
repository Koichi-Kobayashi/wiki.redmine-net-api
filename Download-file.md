Download attachment file.

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

           var url = $"{host}/attachments/download/{<attachment-id>}/{<attachment-file-name>}";
           var document = manager.DownloadFile(url);  

           if (document!= null)
               Console.WriteLine("Document downloaded successfully.");
           else
               Console.WriteLine("Document is null.");    
        }     
    }
}
```

**Async Example:**

```
using System;
using Redmine.Net.Api;
using Redmine.Net.Api.Types;
using Redmine.Net.Api.Async;
using System.Threading.Tasks;

namespace RedmineTest
{
    class Program
    {
        static RedmineManager manager;
        static async Task Main(string[] args)
        {
           string host = "<host>";
           string apiKey = "<api-key>";

           manager = new RedmineManager(host, apiKey);

           var document = await DownloadFileAsync();
           if (document!= null)
               Console.WriteLine("Document downloaded successfully.");
           else
               Console.WriteLine("Document is null.");         
        }

        static async Task<byte[]> DownloadFileAsync()
        { 
           var url = $"{host}/attachments/download/{<attachment-id>}/{<attachment-file-name>}";
           return await manager.DownloadFileAsync(url);  
        }
    }
}
```