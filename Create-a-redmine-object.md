## Creating an object of type T. ##

When trying to create an object with invalid or missing attribute parameters, you will get RedmineException that contains the corresponding error messages.

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

               Issue issue = new Issue();
               issue.Project = new IdentifiableName() { Id = <project-id> };
               issue.Priority = new IdentifiableName() { Id = <priority-id> };
               issue.Subject = "Example";
               issue.Description = "Description";
               issue.Category = new IdentifiableName() { Id = <category-id> };
               issue.Status = new IdentifiableName() { Id = <status-id> };
               issue.AssignedTo = new IdentifiableName() { Id = <user-id> };
               issue.ParentIssueId = <parent-issue-id>;

               manager.CreateObject(issue);
           }
        }
    }
