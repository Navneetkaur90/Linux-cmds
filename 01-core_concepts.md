 ### To check Linux Version**:  
   `uname -r`

 ---
 ### Hardware related Commands:  
   - **Display CPU information:** 
     `lscpu`
    
   - **Display memory information:**  
     `lsmem`
    
   - **Display block devices( such as USB, disk):**
     `lsblk`

   - **Display comprehensive details about the system's hardware configuration**
     `sudo lshw`

 ---
 ### Init system:
  Once the kernel is fully operational during boot, it searches for an INIT process to start the    user space and the essential system processes.Modern Linux distributions typically use SYSTEMD as the INIT process.
  - **To verify which INIT system is in use**:
   `ls -l  /sbin/init`

 ---
 ### Viewing and Changing Systemd Targets**:  
 Under systemd, traditional runlevels are represented as targets.

   - **View current target:**  
     `systemctl get-default`
    
   - **Change target:**  
      `systemctl set-default [target]`

   - **Common Targets:** 
     - `graphical.target`: For GUI mode.  
     - `multi-user.target`: For command-line mode.

 ---
 ### Identify File Type:  
  In linux, filenames are not required to represent contents of file. In windows, .Jpeg expects a picture file. In linux, .jpeg can be a text file.
   - **Check what kind of file it is:**  
    1. `file <filename>`
    2. Use `ls -l` to see details:  
     - `d`: Directory  
     - `-`: Regular file  
     - `c`, `l`, `p`,`s`,`b`: Special files

---

### **Linux Directory Structure**

   - `/mnt`: Temporary mount point for file systems.  
   - `/tmp`: Stores temporary data.  
   - `/media`: For external media (USB, CDs).  
   - `/bin`: Programs like `cp`, `mv`, `ls`.  
   - `/etc`: Configuration files.  
   - `/var`: Logs and cached data.

---

### **Linux File Systems**
File system defines how data is stored on a disk.Linux File System is structured into directories with specific purpose.

   - `df -h`: disk free : Displays how much available and used storage on disk and where the file system are mounted called mount points.
   - `df -T`: Shows type of file system (regualr,directories,special files)

 **Package Managers**: 
  Linux destributions are categorized based on packag manager they use:
   - Debian-based distributions :  `ubuntu`, `Linux Mint`, `Debian`
     - Debian package manager: `dpkg`, `apt`, `apt-get`.  
   - RPM-based distributions :  `RHEL`, `Fedora`, `CentOS`
     - RPM package manager:  `rpm`, `yum`, `dnf`
 