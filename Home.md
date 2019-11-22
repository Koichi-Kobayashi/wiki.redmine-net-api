redmine-net-api is a library for communicating with a Redmine project management application.

* Uses [Redmine's REST API.](http://www.redmine.org/projects/redmine/wiki/Rest_api/)
* Supports both XML and **JSON(requires .NET Framework 3.5 or higher)** formats.
* Supports GZipped responses from servers.
* This API provides access and basic CRUD operations (create, read, update, delete) for the resources described below:

|Resource  | Read   | Create   | Update   | Delete  |
|:---------|:------:|:--------:|:--------:|:-------:|
 Attachments|O|O|-|-
 Custom Fields|O|-|-|-
 Enumerations  |O|-|-|-
 Files |O|O|-|-
 Groups|O|O|O|O
 Issues  |O|O|O|O
 Issue Categories|O|O|O|O
 Issue Relations|O|O|O|O
 Issue Statuses|O|-|-|-
 News|O|-|-|-
 Projects|O|O|O|O
 Project Memberships|O|O|O|O
 Queries  |O|-|-|-
 Roles |O|-|-|-
 Time Entries |O|O|O|O
 Trackers |O|-|-|-
 Users |O|O|O|O
 Versions |O|O|O|O
 Wiki Pages |O|O|O|O

**How to use redmine-net-api**

Get NuGet package and see wiki for examples on how to use the available functionalities.
