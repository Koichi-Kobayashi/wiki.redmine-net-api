### Download file

Download attachment file.

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

               var url = host + "/attachments/download/" + "<attachment-id>" + "/" + "<attachment-file-name>";
               var document = manager.DownloadFile(url);           
        }
    }