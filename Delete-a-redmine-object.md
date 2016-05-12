#### Deleting an object of type T. ####

For all the types, except the **`IssueCategories`** and **`WikiPage`**, of Redmine .NET Api the delete operation is straight forward. You just need to send the id of the object.

For IssueCategories you can use the optional parameter:
  * **reassign\_to\_id**:  when there are issues assigned to the category you are deleting, this parameter lets you reassign these issues to the category with this id.


**Example:**

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

            manager.DeleteObject<Issue>(issueId, null);
        }
    }
}
```