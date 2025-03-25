### **File and Directory Management**
1. **`pwd`**    : Print the current working directory.
2. **`ls`**     : List files and directories in the current directory.
                 -Options: `-l` (detailed view), `-a` (show hidden files).
3. **`cd`**     : Change directory.
                 -Example: `cd /path/to/directory`
4. **`mkdir`**  : Create a new directory.
                 -Example: `mkdir new_folder`
5. **`rmdir`**  : Remove an empty directory.
6. **`rm`**     : Remove files or directories.
                - Options: `-r` (recursive for directories), `-f` (force deletion).
7. **`cp`**     : Copy files or directories.
                  - Options: `-r` (copy directories).
8. **`mv`**     : Move or rename files or directories.
9. **`touch`**  : Create an empty file or update the timestamp of an existing file.
10. **`find`**  : Search for files in a directory hierarchy.
11. **`locate`**: Find a file by searching a pre-built database.

---

### **Viewing and Editing Files**
12. **`cat`**  : Display the contents of a file.
13. **`tac`**  : Display the contents of a file in reverse order.
14. **`more`** : View file contents one screen at a time.
15. **`less`** : Similar to `more` but with backward navigation.
16. **`head`** : Display the first few lines of a file.
17. **`tail`** : Display the last few lines of a file.
               - Option: `-f` (follow file updates, useful for logs).
18. **`nano`** : Open a simple text editor in the terminal.
19. **`vim`**  : Open the powerful Vim text editor.
20. **`echo`** : Print text to the terminal or write it to a file.

---

### **File Permissions and Ownership**
21. **`chmod`**  : Change file permissions.
                 - Example: `chmod 755 file`
22. **`chown`**  : Change file ownership.
                 - Example: `chown user:group file`
23. **`ls -l`**  : View file permissions and ownership.
    **`ls -la`** : View file permissions and ownership including hidden

---

### **Process Management**
24. **`ps`**      : Display running processes.
                   - Option: `aux` (detailed process list).
25. **`top`**     : Show real-time system processes and resource usage.
26. **`kill`**    : Terminate a process by PID.
27. **`killall`** : Terminate processes by name.
28. **`bg`**      : Resume a job in the background.
29. **`fg`**      : Resume a job in the foreground.
30. **`jobs`**    : List active background jobs.

---

### **File Compression and Archiving**
31. **`tar`**      : Archive files and directories.
                    - Example: `tar -cvf archive.tar files/`
32. **`gzip`**     : Compress files.
33. **`gunzip`**   : Decompress files compressed with `gzip`.
34. **`zip`**      : Compress files into a `.zip` archive.
35. **`unzip`**    : Extract `.zip` archives.

---

### **Networking**
36. **`ping`**     : Check network connectivity to a host.
37. **`curl`**     : Transfer data from or to a server.
38. **`wget`**     : Download files from the web.
39. **`ifconfig`** : Display network interfaces (deprecated; use `ip`).
40. **`ip`**       : Manage IP addresses and routes.
                   - Example: `ip addr`

---

### **User Management**
41. **`whoami`**  : Show the current logged-in user.
42. **`who`**     : Show who is logged into the system.
43. **`adduser`** : Add a new user.
44. **`passwd`**  : Change a user's password.
45. **`su`**      : Switch user accounts.
46. **`sudo`**    : Run commands with elevated (superuser) privileges.

---

### **System Information**
47. **`uname`**     : Display system information.
                      - Example: `uname -a`
48. **`hostname`**  : Display or set the system hostname.
49. **`df`**        : Show disk space usage.
50. **`du`**        : Show file or directory size.
                     - Example: `du -sh /path`
51. **`free`**      : Display memory usage.
52. **`uptime`**    : Show system uptime.
53. **`dmesg`**     : Display system boot and kernel logs.
54. **`date`**      : Show or set the current date and time.
55. **`cal`**       : Display a calendar.

---

### **Package Management**
(Varies by distribution)
56. **`apt`** (Debian/Ubuntu): Manage packages.
   - Example: `sudo apt update && sudo apt install package`

57. **`yum`/`dnf`** (RHEL/Fedora): Manage packages.
   - Example: `sudo yum install package`

58. **`pacman`** (Arch Linux): Manage packages.
   - Example: `sudo pacman -S package`

---

### **Miscellaneous**
59. **`clear`**       : Clear the terminal screen.
60. **`history`**     : Show the command history.
61. **`alias`**       : Create shortcuts for commands.
                      - Example: `alias ll='ls -l'`
62. **`exit`**        : Close the terminal or log out of the session.
63. **`reboot`**      : Restart the system.
64. **`shutdown`**    : Shut down the system.


