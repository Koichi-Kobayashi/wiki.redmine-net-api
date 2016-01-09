## Readmine .NET Api (1.0.0 - pre1)

* Fixed: GetCurrentUserAsync error by adding key to async web client.
* Fixed: Typo error in issue tests.
* Fixed: Clone issue custom fields list.
* Fixed: Create project issue.
* Fixed: Done_ratio empty issue.
* Fixed: XML - User custom fields issue.
* Fixed: XML - Set is_private attribute issue.
* Fixed: XML - Issue with adding issues.
* Fixed: JSON - Add ProjectMembership is not working.
* Fixed: JSON - Get ProjectMembership returns null.
* Fixed: Project trackers.
* Fixed: JSON - Enabled module names project converter.
* Fixed: JSON - Upload converter issue.
* Fixed: Set parent to null at project update.
* Fixed: Filter users by group.

* Added multiple watchers on issue

* Async request refactored. 

# Broken changes

* Renamed AddUser to AddUserToGroup.
* Renamed DeleteUser to DeleteUserFromGroup.
* Renamed AddWatcher to AddWatcherToIssue.
* Renamed RemoveWatcher to RemoveWatcherFromIssue.
* Renamed class RedmineSerialization to RedmineSerializer.
* ToXML &lt;T&gt;, FromXML&lt;T&gt; methods are not longer visible. 

* Removed GetUsers

