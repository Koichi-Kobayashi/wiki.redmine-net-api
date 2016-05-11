## Uploading a file as attachment to an issue.

#### Example: ####
```
using System;
using System.Collections.Specialized;
using Redmine.Net.Api;
using Redmine.Net.Api.Types;

namespace RedmineTest
{
    class Program
    {
        RedmineManager redmineManager;
        static void Main(string[] args)
        {
            string host = "<host>";
            string apiKey = "<apikey>";
            redmineManager = new RedmineManager(host, apiKey);
            UploadAttachment();
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