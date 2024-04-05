# API Documentation

_This Documentation has been written by [c4vxl](https://c4vxl.de/)!_
_Last Change: 4.5.2024_

## Table of contents
1. [Getting Started](#getting-started)
2. [About](#about-this-documentation)
3. [Basic Layout of API Calls](#basic-layout-of-api-calls)
4. [File System](#file-system)
- <details>
  <summary>Expand</summary>
  
    - [Listing Files and Folders](#listing-files-and-folders)
    - [Downloading Files](#downloading-files)
    - [Set File Content](#set-file-content)
    - [Uploading a file](#uploading-a-file)
    - [Creating a File](#creating-a-file)
    - [Creating a Folder](#creating-a-folder)
    - [Deleting a Path](#deleting-a-path)
    - [Compile](#compile)
    - [Decompile](#decompile)
    - [Rename](#rename)
    - [Move](#move)
</details>

5. [Account System](#account-system)
- <details>
  <summary>Expand</summary>
  
    - [Get Account Info](#get-account-info)
    - [Upload Profile Picture](#upload-profile-picture)
    - [Set Account Status](#set-account-status)
    - [Check if Account is Valid](#check-if-account-is-valid)
</details>

6. [Backup System](#backup-system)
- <details>
  <summary>Expand</summary>
  
    - [List Backups](#list-backups)
    - [Creating a Backup](#creating-a-backup)
    - [Deleting a Backup](#deleting-a-backup)
    - [Loading a Backup](#loading-a-backup)
</details>


## Getting Started
Welcome to the c4vxl Cloud API documentation! This API allows you to unlock the full potential of c4vxl Cloud by providing seamless integration and extending the capabilities of our cloud platform to suit your specific needs. Whether you're building applications, automating workflows, or enhancing user experiences, our API empowers you with direct access to the core features of our cloud service.

<br>

### About this Documentation
This documentation provides comprehensive information on the c4vxl Cloud API. Here, you will find detailed explanations of various API endpoints, along with sample code snippets demonstrating how to use them in your applications.

All examples and code snippets provided in this documentation are written in JavaScript. However, you can adapt these examples to suit your preferred programming language or environment as needed.

<br>

Every Response from the API will be in JSON Format and will __always__ contain the following variables:
- `success`: _Boolean_ indicating if the performed Action was successfull
- `content`: _Array or String_ the content the api passed to the requester

In case of an error, the API will send the following variables as well:
- `error`: _Int_ The id of the Error (Error Code)
- `error_message`: _String_ Short description of the issue


### Basic Layout of API Calls
Each API call to c4vxl Cloud needs to include the following parameters:

- `request`: _Specifies the type of request being made._
- `username`: _Your username for accessing the c4vxl Cloud service._
- `password`: _Your password for accessing the c4vxl Cloud service._

Below is a basic layout of how each API call should be structured:

```javascript
const formData = new FormData();
formData.append("request", "{request_type_here}");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
// Additional parameters specific to the request type can be appended here

// Make a fetch request to the c4vxl Cloud API endpoint
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```


---

# File System
The File System section of the API documentation outlines various endpoints and methods for interacting with the file storage system of the c4vxl Cloud platform. These endpoints allow users to perform operations such as listing files and folders, downloading and uploading files, creating and deleting files and folders, as well as compiling and decompiling files.

#### Listing Files and Folders
Retrieve a list of files in a specified directory.

- Request: `filesystem_list`
- Method: `POST`
- Variables:
    - `path`: Pass the path of the directory to list files

###### Example
```javascript
const formData = new FormData();
formData.append("request", "filesystem_list");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
formData.append("path", "{path_you_want_to_list}");

var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Downloading Files
Retrieve a file's content from a specified path.

- Request: `filesystem_download`
- Method: `POST`
- Variables:
    - `path`: Pass the path to your file

###### Example
```javascript
const formData = new FormData();
formData.append("request", "filesystem_download");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
formData.append("path", "{path_to_file}");

var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Set File Content
Set the content of a specified file.

- Request: `filesystem_set_file_content`
- Method: `POST`
- Variables:
    - `path`: Pass the path to your file
    - `newContent`: Pass the new content for your file

###### Example
```javascript
const formData = new FormData();
formData.append("request", "filesystem_set_file_content");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
formData.append("path", "{path_to_file}");

var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Uploading a file
Upload a file to a specified destination.

- Request: `filesystem_upload`
- Method: `POST`
- Variables:
    - `file`: Pass the file to upload
    - `dest`: Pass the destination directory for your file

###### Example
```javascript
const formData = new FormData();
formData.append("request", "filesystem_upload");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
formData.append("file", "{your_file}");
formData.append("dest", "{destination}");

var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Creating a File
Create a file at a specified path.

- Request: `filesystem_create_file`
- Method: `POST`
- Variables:
    - `path`: Pass the path to your file

###### Example
```javascript
const formData = new FormData();
formData.append("request", "filesystem_create_file");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
formData.append("path", "{your_file_path}");

var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Creating a Folder
Create a Folder at a specified path.

- Request: `filesystem_create_folder`
- Method: `POST`
- Variables:
    - `path`: Pass the path to your folder

###### Example
```javascript
const formData = new FormData();
formData.append("request", "filesystem_create_folder");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
formData.append("path", "{your_folder_path}");

var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Deleting a Path
This endpoint allows you to delete a file or folder at a specified path.

- Request: `filesystem_delete`
- Method: `POST`
- Variables:
    - `path`: Pass the path to your file or folder

###### Example
```javascript
const formData = new FormData();
formData.append("request", "filesystem_delete");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
formData.append("path", "{your_path}");

var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Compile
This endpoint allows you to compile a file at a specified path.

- Request: `filesystem_compile`
- Method: `POST`
- Variables:
    - `path`: Pass the path to your folder

###### Example
```javascript
const formData = new FormData();
formData.append("request", "filesystem_compile");
formData.append("path", "{your_file_path}");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
        
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Decompile
This endpoint allows you to decompile a .zip file at a specified path.

- Request: `filesystem_decompile`
- Method: `POST`
- Variables:
    - `path`: Pass the path to your file

###### Example
```javascript
const formData = new FormData();
formData.append("request", "filesystem_decompile");
formData.append("path", "{your_file_path}");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
        
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Rename
This endpoint allows you to rename a file or folder at a specified path.

- Request: `filesystem_rename`
- Method: `POST`
- Variables:
    - `path`: Pass the path to your file
    - `newName`: : Pass the new name for the file or folder

###### Example
```javascript
const formData = new FormData();
formData.append("request", "filesystem_rename");
formData.append("path", "{your_file_or_folder_path}");
formData.append("newName", "{new_name_here}");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
        
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Move
This endpoint allows you to move a file or folder from one location to another.

- Request: `filesystem_move`
- Method: `POST`
- Variables:
    - `path`: Pass the path to your file or folder
    - `dest`: : Pass the destination

###### Example
```javascript
const formData = new FormData();
formData.append("request", "filesystem_move");
formData.append("path", "{your_file_or_folder_path}");
formData.append("dest", "{your_destination_path}");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
        
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

---

# Account System
The Account System section details endpoints related to managing user accounts within the c4vxl Cloud platform. Users can retrieve account information, upload profile pictures, set account status, and check if an account is valid using these endpoints.

#### Get Account Info
This endpoint allows you to retrieve information about an account based on the UUID.

- Request: `account_info`
- Method: `POST`
- Variables:
    - `uuid`: Pass the uuid of your account

###### Example
```javascript
const formData = new FormData();
formData.append("request", "account_info");
formData.append("uuid", "{account_uuid}");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
        
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Upload Profile Picture
This endpoint allows you to upload a new profile picture.

- Request: `account_upload_profile_picture`
- Method: `POST`
- Variables:
    - `file`: Pass the image for your profile picture

###### Example
```javascript
const formData = new FormData();
formData.append("request", "account_upload_profile_picture");
formData.append("file", {your_file});
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
        
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Set Account Status
This endpoint allows you to set a new status for the account.

- Request: `account_set_status`
- Method: `POST`
- Variables:
    - `newStatus`: Pass the new content of your status

###### Example
```javascript
const formData = new FormData();
formData.append("request", "account_set_status");
formData.append("newStatus", "{new_status_here}");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
        
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Check if Account is Valid
This endpoint allows you to check if the account is valid.

- Request: `account_is_valid`
- Method: `POST`
- Variables: `NONE`

###### Example
```javascript
const formData = new FormData();
formData.append("request", "account_is_valid");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
        
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

---

# Backup System
In the Backup System section, users can find endpoints for managing backups of their data on the c4vxl Cloud platform. These endpoints enable users to list available backups, create new backups, remove existing backups, and load backups as needed.

#### List Backups
This endpoint allows you to retrieve a list of available backups.

- Request: `backups_list`
- Method: `POST`
- Variables: `NONE`

###### Example
```javascript
const formData = new FormData();
formData.append("request", "backups_list");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
        
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Creating a Backup
This endpoint allows you to create a new backup.

- Request: `backups_create`
- Method: `POST`
- Variables: `NONE`

###### Example
```javascript
const formData = new FormData();
formData.append("request", "backups_create");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
        
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Deleting a Backup
This endpoint allows you to remove a specific backup by providing its index.

- Request: `backups_create`
- Method: `POST`
- Variables: `NONE`

###### Example
```javascript
const formData = new FormData();
formData.append("request", "backups_remove");
formData.append("backupId", "{backup_index}");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
        
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```

<br>

#### Loading a Backup
This endpoint allows you to load a specific backup by providing its index.

- Request: `backups_create`
- Method: `POST`
- Variables:
    - `backupId`: Pass the index of the backup you want to load

###### Example
```javascript
const formData = new FormData();
formData.append("request", "backups_load");
formData.append("backupId", "{backup_index}");
formData.append("username", "{your_username}");
formData.append("password", "{your_password}");
        
var response = await fetch("https://cloud.c4vxl.de/cloud/api/", {
    method: "POST",
    body: formData
});
```
