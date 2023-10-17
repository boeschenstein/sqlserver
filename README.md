# MS SQL Server

## Install LocalDB (?)

### Install LocalDB using media (?)

<https://learn.microsoft.com/en-us/sql/database-engine/configure-windows/sql-server-express-localdb?view=sql-server-ver16>

- download SQL Server Installer (full)
- run installer, Select "Download Media"
- \media\1033_ENU_LP\x64\Setup\x64\SqlLocalDB.msi
- but how to install ??
 
### Install Sql Server Express or Developer (?)

- download SQL Server Installer (full)
- run installer, select "Express" (not "Developer")
  - option Express shows "Shared Feature" = "LocalDB"
  - Develper is also a good option, but does not contain "LocalDB"
- installed it, but connection to (LocalDB)\MSSQLLocalDB was not possible... no db available?

### fix LocalDB

Error: Unable to connect to (localdb)\MSSQLLocalDB - Due to trigger execution

Fix from <https://stackoverflow.com/questions/66080953/unable-to-connect-to-localdb-mssqllocaldb-due-to-trigger-execution>

SqlLocalDB stop MSSQLLocalDB -k
SqlLocalDB delete MSSQLLocalDB
SqlLocalDB create MSSQLLocalDB -s

Now Login to (LocalDB)\MSSQLLocalDB works.

## Create Login and User

```sql
--Make sure to use the MASTER database when you create logins and make sure the login is ENABLED.

USE MASTER
GO

CREATE LOGIN NewLogin WITH PASSWORD=N'NewPassword1!', DEFAULT_DATABASE = MASTER, DEFAULT_LANGUAGE = US_ENGLISH
GO

ALTER LOGIN NewLogin ENABLE
GO

--After creating a Login, you can now create a user and add the user to the new Login:

USE test
GO

CREATE USER NewUserName FOR LOGIN NewLogin WITH DEFAULT_SCHEMA = [DBO]
GO

-- todo : grant db_dataread to user/login
```
