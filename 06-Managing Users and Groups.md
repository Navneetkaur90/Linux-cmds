## Linux Accounts and Access Control Files:
| **Category**        | **Description**                                                                                           | **Access Control File**                | **Access Command**                 |
|----------------------|-----------------------------------------------------------------------------------------------------------|-------------------------|-------------------------------------|
| **User Accounts**    | Stores information about users, including username, UID, GID, home directory, and default shell.         | `/etc/passwd`           | `cat /etc/passwd`                  |
| **Group Accounts**   | Lists group names and the users belonging to each group.e.g: GID                                                 | `/etc/group`            | `cat /etc/group`                   |
| **User Passwords** | Contains encrypted user passwords; restricted to root for security.                                      | `/etc/shadow`           | `sudo cat /etc/shadow`             |
| **Sudo Configuration** |default `sudo` configuration; use `visudo` for safe editing.                                  | `/etc/sudoers`          | `cat etc/sudoers`                      |

**Important:**
- Never edit the `/etc/sudoers` file directly.
- Always use the `visudo` command to edit it safely. `visudo` locks the file to prevent concurrent edits and performs syntax checking.
- Only users listed in `sudoers` file can make use of sudo for privilege escalation.
---

## Linux User and Group Management Commands
**Account Types:**
* **Root User:** Superuser account with unrestricted privileges (UID 0).
* **System Accounts:** Used by the operating system and services ( `<UID 100 or b/w 500-1000`).
    *  Often created during OS installation.
    * **Examples:** `ssh`, `mail`
    * **Service Accounts:** Used by specific applications or services when get installed (often have limited privileges). Example- Nginx service uses SA called nginx.
* **Normal User Accounts:** Created for individual users.

**Basic User Information Commands:**
1.  **`id <user>`**: Get user details (UID, GID, groups).
2.  **`who`**: List users currently logged in.
3.  **`last`**: Display a record of all logged-in users.
4.  **`whoami`**: User currently logged in.
5.  **`useradd`** useradd <username> For more control and scripting, where you need to specify all parameters explicitly, useradd is more suitable.
6.  **`userdel`**: userdel username
7.  **`adduser`**: It handles the common setup tasks automatically. (system generated UID,GID)
