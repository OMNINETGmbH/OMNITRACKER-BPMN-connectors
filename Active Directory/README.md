# Omnitracker Connector Package
This connector package offers additional features for various purposes using PowerShell as the primary language.

## Version 2 ##

## Features:
- Add Active Directory User
- Add Active Directory User Group
- Delete Active Directory User Group
- Modify Active Directory User
- Delete Active Directory User
- Reset Password
- Lock Active Directory User
- Unlock Active Directory User
- Add Active Directory User to Usergroup
- Remove Active Directory User from Usergroup
- Export Active Directory Users
- Export Active Directory Usergroups
- Export Computernames

## Connectors

### 1. Add Active Directory User Group
Add Active Directory User Group

**Inputs**:
- `Group name (String)`: Name of the Active Directory Group.
- `Path (String)`: Path of the Active Directory, Please use this form: 'OU=Users,OU=Sitename,DC=omnitracker,DC=com'.
- `Server (String)`: Servername.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

**Outputs:** None mentioned.

### 2. Delete Active Directory User Group
Delete Active Directory User Group

**Inputs**:
- `Group name (String)`: Name of the Active Directory Group.
- `Path (String)`: Path of the Active Directory, Please use this form: 'OU=Users,OU=Sitename,DC=omnitracker,DC=com'.
- `Server (String)`: Servername.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

**Outputs:** None mentioned.

### 3. Add Active Directory User
Add Active Directory User

**Inputs**:
- `Name (String)`: Name of the Active Directory User.
- `Password (String)`: Password of the Active Directory User.
- `Email (String)`: Email  of the Active Directory User.
- `Path (String)`: Path of the Active Directory, Please use this form: 'OU=Users,OU=Sitename,DC=omnitracker,DC=com'.
- `Server (String)`: Servername.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

**Outputs:**
- `HasErrorOut (Boolean)`: Indicates if an error has occurred.
- `ErrorMessage (String)`: Contains an error message if any error has occurred.

### 4. Modify Active Directory User
Modify Active Directory User

**Inputs**:
- `Name (String)`: Name of the Active Directory User.
- `Password (String)`: Password of the Active Directory User.
- `Email (String)`: Email  of the Active Directory User.
- `Path (String)`: Path of the Active Directory, Please use this form: 'OU=Users,OU=Sitename,DC=omnitracker,DC=com'.
- `Server (String)`: Servername.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

**Outputs:**
- `HasErrorOut (Boolean)`: Indicates if an error has occurred.
- `ErrorMessage (String)`: Contains an error message if any error has occurred.

### 5. Delete Active Directory User
Delete Active Directory User

**Inputs**:
- `Name (String)`: Name of the Active Directory User.
- `Server (String)`: Servername.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

**Outputs:** None mentioned.

### 6. Reset Password
Reset Password of Active Directory User at next logon

**Inputs**:
- `Name (String)`: Name of the Active Directory User.
- `Path (String)`: Path of the Active Directory, Please use this form: 'OU=Users,OU=Sitename,DC=omnitracker,DC=com'.
- `Server (String)`: Servername.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

### 7. Lock Active Directory User
Lock Active Directory User

**Inputs**:
- `Name (String)`: Name of the Active Directory User.
- `Path (String)`: Path of the Active Directory, Please use this form: 'OU=Users,OU=Sitename,DC=omnitracker,DC=com'.
- `Server (String)`: Servername.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

**Outputs:** None mentioned.

### 8. Unlock Active Directory User
Unlock Active Directory User

**Inputs**:
- `Name (String)`: Name of the Active Directory User.
- `Path (String)`: Path of the Active Directory, Please use this form: 'OU=Users,OU=Sitename,DC=omnitracker,DC=com'.
- `Server (String)`: Servername.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

**Outputs:** None mentioned.

### 9. Add Active Directory User to Usergroup
Add Active Directory User to Usergroup

**Inputs**:
- `Name (String)`: Name of the Active Directory User.
- `Group name (String)`: Name of the Active Directory Group.
- `Path (String)`: Path of the Active Directory, Please use this form: 'OU=Users,OU=Sitename,DC=omnitracker,DC=com'.
- `Server (String)`: Servername.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

**Outputs:** None mentioned.

### 10. Remove Active Directory User from Usergroup
Remove Active Directory User from Usergroup

**Inputs**:
- `Name (String)`: Name of the Active Directory User.
- `Group name (String)`: Name of the Active Directory Group.
- `Path (String)`: Path of the Active Directory, Please use this form: 'OU=Users,OU=Sitename,DC=omnitracker,DC=com'.
- `Server (String)`: Servername.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

**Outputs:** None mentioned.

### 11. Export Active Directory Users
Export Active Directory Users to *.csv File

**Inputs**:
- `Path (String)`: Path of the Active Directory, Please use this form: 'OU=Users,OU=Sitename,DC=omnitracker,DC=com'.
- `Server (String)`: Servername.
- `Export File path (String)`: Insert export file path 'C:\export-file-name.csv'.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

**Outputs:** None mentioned.

### 12. Export Active Directory Usergroups
Export Active Directory Usergroups to *.csv File

**Inputs**:
- `Path (String)`: Path of the Active Directory, Please use this form: 'OU=Users,OU=Sitename,DC=omnitracker,DC=com'.
- `Server (String)`: Servername.
- `Export File path (String)`: Insert export file path 'C:\export-file-name.csv'.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

**Outputs:** None mentioned.

### 13. Export Computernames
Export Computernames from Active Directory to *.csv File

**Inputs**:
- `Path (String)`: Path of the Active Directory, Please use this form: 'OU=Users,OU=Sitename,DC=omnitracker,DC=com'.
- `Server (String)`: Servername.
- `Export File path (String)`: Insert export file path 'C:\export-file-name.csv'.
- `Server administrator (String)`: Target Server administrator.
- `Server administrator password (String)`: Target Server administrator password.

**Outputs:** None mentioned.

## Note:
For some connectors, error handling mechanisms are in place. If an error occurs during the execution of any connector, the outputs `strHasErrorOut` will be set to true and `ErrorMessage` will contain the corresponding error message.
