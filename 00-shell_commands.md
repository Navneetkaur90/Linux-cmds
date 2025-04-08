### Types of Linux Shells
- **Most Common:** Bash Shell

---

### Commands and Their Usage

#### **1. `pwd`**
- Displays the current working directory.

#### **2. `ls`**
- Lists files and directories in the current directory.
**`ls` Options:**
  - `ls -l`: Provides a long listing format with more file details.
  - `ls -a`: Lists all files, including hidden ones.
  - `ls -lt`: Lists files in the order they were created.
  - Combine options for detailed file information.

#### **3. `mkdir`**
- Creates new directories.
- **Example:** `mkdir Dir1 Dir2 Dir3` (Creates multiple directories at once)
- **`-p` option:** Creates parent directories if they don’t exist.  
  Example: `mkdir -p India/mumbai`

#### **4. `cd`**
- Changes the current directory.
- Without arguments: Returns to the home directory.
- Example:  
  - `cd India/Mumbai` (Navigates to the "Mumbai" directory inside "India")  
  - `cd ..` (Goes one level up)

#### **5. `pushd` and `popd`**
- **`pushd`:** Pushes the current directory to the stack and switches to it  
- **`popd`:** Pops a directory off the stack and switches back to it.

#### **6. `mv`**
- Moves or renames files/directories.
- **Usage:**  
  `mv <source_path> <destination_path>`  
  Example: `mv India/Ontario Canada/`
  Rename dir: `mv Asia/India/Mumbai Asia/India/MumbaiCorrected/`
  
#### **7. `cp`**
- Copies files.
- **By default:** Works only with files, not directories.  
  - **Usage:** `cp file1.txt file2.txt` or `cp file1.txt /path/to/destination/`
  - To copy directories, use the `-r` option:  
    Example: `cp -r Asia/India/Mumbai Africa/Egypt/` This copies the entire Mumbai directory into Africa/Egypt/.

#### **8. `cat`**
  - **Read file contents:** `cat <file_name>`
  - **Edit file contents:** Combine `cat` with redirection (`>` or `>>`).  
    Example: `cat > file_name`  
    The terminal will prompt you for input.

#### **9. `rm`**
- Removes files or directories.
- To remove directories, use the `-r` option.  
  Example: `rm -r directory_name`

#### **10. `touch`**
  - Create a new file:`touch <file_path>`  
    Example: `touch /home/user/hello.txt`
---
### Features of Bash
1. **Command Auto-completion:** Use `Tab` + `spacke key`
2. **Aliases:** Shortcuts for commands.  
   Example: `alias dt=date`
3. **Command History:** Use `history` to list previously executed commands.
4. **Environment Variables:** Manage environment variables using `env`.
---
### Notes
- **Root Directory:** `/`  
  Used as the base for absolute paths.
- **Relative Paths:** Paths relative to the current directory.
- **Recursive Copy:** Use `cp -r` to copy directories and their contents.
---
### Getting Help with Commands
- **`whatis`:** Provides a brief description of a command.  
  Example: `whatis date`
- **`man`:** Displays detailed information about a command. Man pages are manuals that are by default built into most Linux operating systems.
  Example: `man date`
- **`-h` or `--help`:** Shows help options for a command.  
 
---

### Environment Variables in Linux
- **To list all environment variables:**  type`env`
- **Examples:**
  - `echo $HOME` → Displays the home directory.
  - `echo $SHELL` → Displays the shell currently in use.

### Creating Environment Variables
- **Command:** `export variable_name=value`  
  Example: `export office=Caledon`
- **Making it Persistent:**  
  Add the variable to configuration files such as:
  - `~/.profile`
  - `~/.bash_profile`
  - `~/.bashrc`
---

### Persisting Configuration Changes
- To ensure customizations (e.g., aliases, variables) persist across sessions, add them to configuration files such as:
  - `~/.profile`
  - `~/.bash_profile`
  - `~/.bashrc`
---

### Bash Prompt Customization
- **Controlled by the `PS1` variable.**
  - View current prompt: `echo $PS1`
  - Example prompt format:  
    `PS1="[\d \u@\h:\w] $ "`  
    - `\d` → Date  
    - `\u` → Username  
    - `\h` → Hostname  
    - `\w` → Current working directory  
  - Customize by editing `PS1`.

---

### Redirection Operators
1. **`>`** → Redirects and overwrites the content of a file.  
2. **`>>`** → Redirects and appends to the content of a file. 
---

### IMPORTANT difference
1. **`Inside " "`** → Double qoutes allow interpretation.Variables and special chars are interpreted by shell
2.  **`Inside ' '`** → Single quotes prevent interpretation(treat as plain text)
---
### Command Type 
To verify whether a linux command is internal or external, use the type command. 
For example, executing type echo shows that echo is a built-in command.
---

### **Linux Core Concepts**

1. **Check Linux Version**:  
   ```bash
   uname -r
   ```

2. **Viewing and Changing Systemd Targets**:  
   - View current target:  
     ```bash
     systemctl get-default
     ```
   - Change target:  
     ```bash
     systemctl set-default [target]
     ```
   - Common Targets:  
     - `graphical.target`: For GUI mode.  
     - `multi-user.target`: For command-line mode.

3. **System Information Commands**:  
   - Display CPU information:  
     ```bash
     lscpu
     ```
   - Display memory information:  
     ```bash
     lsblk
     ```

4. **Identify File Type**:  
   - Check what kind of file it is:  
     ```bash
     file <filename>
     ```
   - Use `ls -l` to see details:  
     - `d`: Directory  
     - `-`: Regular file  
     - `c`, `l`, `p`, `b`: Special files

---

### **Linux Directory Structure**

1. **Common Directories**:
   - `/mnt`: Temporary mount point for file systems.  
   - `/tmp`: Stores temporary data.  
   - `/media`: For external media (USB, CDs).  
   - `/bin`: Programs like `cp`, `mv`, `ls`.  
   - `/etc`: Configuration files.  
   - `/var`: Logs and cached data.

2. **Mounted File Systems**:
   - View details:  
     ```bash
     df -h
     ```
     (`-h` flag: human-readable format).

---

### **Linux File Systems**

1. **Types of File Systems**:
   - `df`: Displays available and used storage.  
   - `df -T`: Shows type of file system.

2. **File Managers**:
   - Debian-based:  
     - `dpkg`, `apt`, `apt-get`.  
   - RPM-based:  
     - `rpm`, `yum`, `dnf`.

---

### **Disk Usage and File Size**

1. **Check File/Directory Size**:
   - General usage:  
     ```bash
     du
     ```
   - Human-readable format:  
     ```bash
     du -sh
     ```
   - Check file size:  
     ```bash
     ls -lh
     ```

---

### **Archiving Files**

1. **Using `tar`**:
   - Create an archive:  
     ```bash
     tar -cf <archive_name.tar> <files/directories>
     ```
   - View archive contents:  
     ```bash
     tar -tf <archive_name.tar>
     ```
   - Extract archive contents:  
     ```bash
     tar -xf <archive_name.tar>
     ```
   - Compress archive:  
     ```bash
     tar -zcf <archive_name.tar.gz> <files/directories>
     ```

2. **Compression Tools**:
   - **Compressing**:  
     - `bzip2`: Adds `.bz2` extension.  
     - `gzip`: Adds `.gz` extension.  
     - `xz`: Adds `.xz` extension.
   - **Uncompressing**:  
     - `bunzip2`, `gunzip`, `unxz`.

3. **View Compressed Files**:
   - Without extracting:  
     ```bash
     bzcat, zcat, xzcat
     ```

