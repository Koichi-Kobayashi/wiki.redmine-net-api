#### Deleting an object of type T. ####

For all the types, except the **`IssueCategories`** and **`WikiPage`**, of Redmine .NET Api the delete operation is straight forward. You just need to send the id of the object.

For IssueCategories you can use the optional parameter:
  * `reassign_to_id`:  when there are issues assigned to the category you are deleting, this parameter lets you reassign these issues to the category with this id.


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
            string issueId = "<issue-id>";
            var manager = new RedmineManager(host, apiKey);

            try
            {
               manager.DeleteObject<Issue>(issueId, null);
            }
            catch(NotFoundException nfe)
            {
              Console.WriteLine("Object not found.");
              return;
            }
            catch(RedmineException rex)
            {
              Console.WriteLine("Delete object returned exception {0}.", rex.Message);
              return;
            }

            try
            { 
              manager.GetObject<Issue>(issueId, null);
            }
            catch(NotFoundException nfe)
            {
              Console.WriteLine("Object deleted successfully.");
              return;
            }
            catch(RedmineException rex)
            {
              Console.WriteLine("Get object returned error {0}.", rex.Message);
              return;
            }

            Console.WriteLine("Object was not deleted.");
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
        static void Main(string[] args)
        {
            string host = "<host>";
            string apiKey = "<api-key>";
            manager = new RedmineManager(host, apiKey);

            DeleteObject.Wait();   
        }

        public static async Task DeleteObject()
        {
            string issueId = "<issue-id>";

            try
            {
               await manager.DeleteObjectAsync<Issue>(issueId, null);
            }
            catch(NotFoundException nfe)
            {
              Console.WriteLine("Object not found.");
              return;
            }
            catch(RedmineException rex)
            {
              Console.WriteLine("Delete object returned exception {0}.", rex.Message);
              return;
            }
            Console.WriteLine("Object deleted successfully.");
        }
    }
}
```