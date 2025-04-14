 ### To check Linux Version:  
   `uname -r`

 ---
 ### Hardware related Commands:  
   - Display cpu information:`lscpu`
    
   - Display memory information:`lsmem`
    
   - Display block devices( such as USB, disk):
     `lsblk`

   - Display comprehensive details about the system's hardware configuration:
     `sudo lshw`

 ---
 ### Init system:
  Once the kernel is fully operational during boot, it searches for an INIT process to start the    user space and the essential system processes.Modern Linux distributions typically use SYSTEMD as the INIT process.
  - **To verify which INIT system is in use**:
   `ls -l  /sbin/init`

 ---
 ### Viewing and Changing Systemd Targets:  
 Under systemd, traditional runlevels are represented as targets.

   - **View current target:**  
     `systemctl get-default`
    
   - **Change target:**  
      `systemctl set-default [target]`

   - **Common Targets:** 
     - `graphical.target`: For GUI mode.  
     - `multi-user.target`: For command-line mode.

 ---
 ### **Linux File Systems**
File system defines how data is stored on a disk.Linux File System is structured into directories with specific purpose.
 ### **File System Types**
 - **ext4**: Common default file system for Linux.
 - **xfs, btrfs, ZFS**: Advanced file systems with features like snapshots and better performance.
 - **NFS, CIFS**: For network file systems.


  ### Commands:
   - `df -h`: disk free : Displays how much available and used storage on disk and where the file system are mounted called mount points.
   - `df -T`: Shows type of file system (regualr,directories,special files)

 ### Identify File Type:  
  In linux, filenames are not required to represent contents of file. In windows, .Jpeg expects a picture file. In linux, .jpeg can be a text file.
   - **Check what kind of file it is:**  
    1. `file <filename>`
    2.  Use `ls -l` to see details:  
     - `d`: Directory  
     - `-`: Regular file  
     - **Symbolic Links (`l`)**: Pointers to other files or directories.
     - **Special Files**:
     - **Device Files (`b` or `c`)**: Represent block or character devices (e.g., `/dev/sda`).

### **Linux Directory Structure**
   - `/`   : (Root)The starting point of the file system.
   - `/mnt`: Temporary mount point for file systems.  
   - `/etc`: Configuration files for the system and installed software.
   - `/var`: Logs and cached data.
   - `/bin`: Contains essential binary executables (Programs like `cp`, `mv`, `ls`, `cat`, `mkdir`).
   - `/sbin`: Holds system binaries for administrative tasks (e.g., `fsck`, `reboot`).
   - `/tmp`: Stores temporary data.  
   - `/media`: For external media (USB, CDs).  
   - `/home`: User-specific directories where personal files are stored (e.g., `/home/user`).
   - `/lib` and `/lib64`: Shared libraries and kernel modules.
   - `/usr`: User-level binaries, libraries, documentation, and source code.
   - `/tmp`: Temporary files created by programs; often cleared upon reboot.
   - `/proc` and `/sys`: Virtual filesystems providing information about system processes and hardware.

---

 ### **Package Managers**: 
  Linux destributions are categorized based on packag manager they use:
   - Debian-based distributions :  `ubuntu`, `Linux Mint`, `Debian`
     - Debian package manager: `dpkg`, `apt`, `apt-get`.  
   - RPM-based distributions :  `RHEL`, `Fedora`, `CentOS`
     - RPM package manager:  `rpm`, `yum`, `dnf`
 