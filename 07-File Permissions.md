## Modifying File Permissions (`chmod`):
To change user's home dir,login shell and group affiliations, changing primary group of user ; use chmod
```bash
chmod <permissions> <file>
```
* **Symbolic Notation:**
    * `u`: user (owner)
    * `g`: group
    * `o`: other
    * `a`: all (user, group, other)
    * `+`: add permission
    * `-`: remove permission
    * `r`: read (4)
    * `w`: write (2)
    * `x`: execute (1)
* **Examples:**
    * `chmod u+rwx test_file`: Add read, write, and execute permissions for the owner.
    * `chmod ugo+r-x test_file`: Add read and Remove execute permission for the all.
    * `chmod o-rwx test_file`: Remove all permissions for others.
    * `chmod u+rwx,g+r-x,o-r test_file`: Set different permissions for user, group, and others.
* **Numeric Notation:**
    * Combine the numeric values for read, write, and execute for each category (owner, group, other).
    * **Example:** `chmod 754 test_file` (owner: rwx (4+2+1=7), group: rx (4+0+1=5), other: r-- (4+0+0=4))
---

### Understanding File Permission Notation
* **`chmod <owner><group><other> <file/dir>`**
    * Owner, Group, Other represent the permissions for each category.
    * Permissions are represented numerically (sum of R, W, X) or symbolically (rwx).
* **Example:**
    * `6` (owner) = `4` (read) + `2` (write) + `0` (execute) = `rw-`
    * `0` (group) = `0` (read) + `0` (write) + `0` (execute) = `---`
    * `0` (other) = `0` (read) + `0` (write) + `0` (execute) = `---`
    * So, `chmod 600` results in `rw-------` permissions.
---

## Changing File Ownership and group(`chown`):
```bash
chown <owner>[:<group>] <file>
```
**Example:**
```bash
chown bob:developer test-file
```
### Change only the group:
```bash
chgrp developers test_file
```
* **Note:** If the group is not provided with `chown`, only the ownership is changed.
* **Important Note on Ownership Change:** Only the superuser (root) can typically change the ownership of a file. Normal users can only change the group of files they own (to a group they are a member of).
---

## Viewing File Permissions and Ownership:
**How to See File Permissions, Ownership of a File After Using `chown`or `chmod`**
* **`ls -l`**: View file permissions.
* **`ls -ld <directory>`**: View permissions of a directory itself (not its contents).

**How to View the Type of Account:**
From UID, you can identify ac/ type:
* **`id <username>`**: Shows the UID, GID, primary group, supplementary group of the specified user.
* **System Users:** Typically have UIDs from `0` to `999`. UID `0` is usually reserved for the `root` user (superuser).
* **Normal Users:** Typically have UIDs starting from `1000` and above.
---

## System Information and Task Scheduling
**`Uptime` Command:**
* Displays key information about how long the system has been running.
* Includes:
    * Current time
    * Uptime since last boot
    * Number of users currently logged in
    * Load averages (system load over the last 1, 5, and 15 minutes)

**`Cron Job`:**
* Allows users to specify a date, time, and frequency to schedule tasks.
* These jobs will run automatically at the defined intervals.
* `Crontab` Command is used to manage cron jobs for individual users.
    * **`crontab -e`**: Opens the user's crontab file in a text editor (usually Vi). This allows you to add, modify, or delete scheduled jobs.
    * **`crontab -l`**: Lists the cron jobs scheduled for the current user.
**Important Reminder about `sudo` with `crontab`:**
* **DO NOT use `sudo` with `crontab -e` or `crontab -l` when you want to schedule jobs for your regular user account.**
* If you use `sudo crontab -e`, the jobs you schedule will be run as the **root user**
* To schedule jobs for a specific user (including root), you can use system-wide cron configuration files (like those in `/etc/cron.d/`) 

**Syntax for cron jobs:**
```
*    *    *   *    *
min hour day month weekday  command /script  
```
**Common Examples:**
**Run a command every hour at the 15th minute:**
 ```
15    * * * * command_to_run
```
 * `15`: At the 15th minute of every hour.
 * `*`: Every hour.
 * `*`: Every day of the month.
 * `*`: Every month of the year.
 * `*`: Every day of the week.
 * `command_to_run`: The command you want to execute.
