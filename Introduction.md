redmine-net-api is a library for communicating with a Redmine project management application.

* Uses [Redmine's REST API.](http://www.redmine.org/projects/redmine/wiki/Rest_api/)
* Supports both XML and **JSON(requires .NET Framework 3.5 or higher)** formats.
* Supports GZipped responses from servers.
* This API provides access and basic CRUD operations (create, read, update, delete) for the resources described below:

Resource | Read | Create | Update | Delete
---------|------|--------|--------|-------
 Attachments|x|x|-|-
 Custom Fields|x|-|-|-
 Enumerations  |x|-|-|-
 Groups|x|x|x|x
 Issues  |x|x|x|x
 Issue Categories|x|x|x|x
 Issue Relations|x|x|x|x
 Issue Statuses|x|-|-|-
 News|x|-|-|-
 Projects|x|x|x|x
 Project Memberships|x|x|x|x
 Queries  |x|-|-|-
 Roles |x|-|-|-
 Time Entries |x|x|x|x
 Trackers |x|-|-|-
 Users |x|x|x|x
 Versions |x|x|x|x
 Wiki Pages |x|x|x|x
