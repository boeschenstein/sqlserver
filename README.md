# MS SQL Server

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
