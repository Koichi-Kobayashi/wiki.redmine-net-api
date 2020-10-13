#### Uploading a file as attachment to an issue. ####

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
        static RedmineManager redmineManager;
        static void Main(string[] args)
        {
            string host = "<host>";
            string apiKey = "<api-key>";
            redmineManager = new RedmineManager(host, apiKey);
            UploadAttachment();
    
            Console.WriteLine("Attachment uploaded successfully.");
        }
     
        public static void UploadAttachment()
        {
            //read document from a specified path
            string documentPath = "<document-local-path>";
            byte[] documentData = File.ReadAllBytes(documentPath);

            //upload attachment to redmine
            Upload attachment = redmineManager.UploadFile(documentData);

            //set attachment properties
            attachment.FileName = "AttachmentUploaded.txt";
            attachment.Description = "File uploaded using REST API";
            attachment.ContentType = "text/plain";

            //create a list of attachments to be added to issue
            IList<Upload> attachments = new List<Upload>();
            attachments.Add(attachment);

            //get project
            var projects = redmineManager.GetObjects<Project>(new NameValueCollection());
            var project =  projects.OfType<IdentifiableName>()
                                   .Where(p => p.Name.Equals("<project-name>"))
                                   .FirstOrDefault();

            //create issue and attach the document
            Issue issueWithAttachment = redmineManager.CreateObject<Issue>(
                                            new Issue 
                                            {
                                                Project = project,
                                                Subject = "Issue with attachment",
                                                Uploads = attachments
                                            });
        }
   }
}
```

**Async Example:**
```
using System;
using System.Collections.Specialized;
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

            await UploadAttachmentAsync();
    
            Console.WriteLine("Attachment uploaded successfully.");
        }
     
        public static async Task UploadAttachmentAsync()
        {
            //read document from a specified path
            string documentPath = "<document-local-path>";
            byte[] documentData = File.ReadAllBytes(documentPath);

            //upload attachment to redmine
            Upload attachment = await manager.UploadFileAsync(documentData);

            //set attachment properties
            attachment.FileName = "AttachmentUploaded.txt";
            attachment.Description = "File uploaded using REST API";
            attachment.ContentType = "text/plain";

            //create a list of attachments to be added to issue
            IList<Upload> attachments = new List<Upload>();
            attachments.Add(attachment);

            //get project
            var projects = await manager.GetObjectsAsync<Project>(new NameValueCollection());
            var project =  projects.OfType<IdentifiableName>()
                                   .Where(p => p.Name.Equals("<project-name>"))
                                   .FirstOrDefault();

            //create issue and attach the document
            Issue issueWithAttachment = await manager.CreateObjectAsync<Issue>(
                                            new Issue 
                                            {
                                                Project = project,
                                                Subject = "Issue with attachment",
                                                Uploads = attachments
                                            });
        }
   }
}
```