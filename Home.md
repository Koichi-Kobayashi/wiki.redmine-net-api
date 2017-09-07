redmine-net-api is a library for communicating with a Redmine project management application.

* Uses [Redmine's REST API.](http://www.redmine.org/projects/redmine/wiki/Rest_api/)
* Supports both XML and **JSON(requires .NET Framework 3.5 or higher)** formats.
* Supports GZipped responses from servers.
* This API provides access and basic CRUD operations (create, read, update, delete) for the resources described below:

Resource | Read | Create | Update | Delete
---------|------|--------|--------|-------
 Attachments|O|O|-|-
 Custom Fields|O|-|-|-
 Enumerations  |O|-|-|-
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

**How to run unit tests**

- **Windows**

  No special configuration requiered.

- **Mac OSX**

  - **Xamarin Studio** select xUniTest-redmine-net45-api project and chose **Options**.

  In the window that appears select __`Run -> Custom Commands -> Execute`__ option and enter the following command (using your own settings):

  `/<path>/packages/xunit.runner.console.2.1.0/tools/xunit.console.exe ${TargetFile}`
  - **Visual Studio Code**