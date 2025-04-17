## Storage in Linux 
* `/dev/` directory contains device files.

* **Block devices** (type of file) are storage devices.
    * Represent physical pieces of hardware that store data (e.g., hard disks, SSDs).
    * Accessed through the `/dev/` directory (e.g., `/dev/sda`, `/dev/sdb`).
    * Managed by the kernel.

**To List Block Devices:**
```bash
lsblk OR ls -l /dev/sd* | grep "b"
```
---
**To Create and Delete Partitions on disks:** 
* **`sudo fdisk  /dev/sda`**: Command line tool to create partition tables.(fdisk works with MBR ,4 fixed disk partitions)
* **`sudo fdisk -l /dev/sda`**: list partition tables.
    * Use with caution.
    * `n`: create a new partition
    * `d`: delete a partition
    * `w`: write changes (very important!)
    * `q`: quit without saving
* **`gdisk /dev/sdb`**: Similar to `fdisk` but for GPT partition tables (recommended for larger disks).
* **`gdisk -l /dev/sdb`**: to list the partition table.
---
**Commonly Used Filesystems:**
* **Extended Filesystem Series (`ext`)**: A standard Linux filesystem. ext2,ext3,ext4(common)
    **Creating and Mounting an ext4 filesystem:**
        ```bash
        mkfs.ext4 /dev/sdb1  # Create an ext4 filesystem on the partition /dev/sdb1
        mkdir /mnt/ext4      # Create a mount point directory
        mount /dev/sdb1 /mnt/ext4 # Mount the filesystem to the mount point
        ```
        
**Key Concepts:**
* **Mount Point:** A directory in the existing filesystem where a storage device (partition or entire disk) is attached and its contents become accessible.
* **MBR (Master Boot Record):** An older type of partition table. Has limitations on the number and size of partitions.
* **GPT (GUID Partition Table):** A more modern partition table standard. Supports larger disks and a greater number of partitions.
---
### Managing Mounted Filesystems and Block Devices
**To check Mounted Filesystems:**

```bash
df -h
```
`-h`: Displays output in a human-readable format (e.g., 1G, 500M).

**To check a specific mounted filesystem (e.g., `/dev/sdb1` mounted at `/mnt/data`):**
  ```bash
  df -h | grep /dev/sdb1
  ```
  OR
  ```bash
  df -P /mnt/data
  ```
`-P`: POSIX output format for better portability.
---
### **Making Mounts Persistent Across Reboots:**
1.  **Add an entry to the `/etc/fstab` file.**
2.  **Syntax for an `/etc/fstab` entry:**
    ```
    <file system> <mount point> <type> <options> <dump> <pass>
    ```
    * `<file system>`: The device name (e.g., `/dev/sdb1`) or UUID of the filesystem.
    * `<mount point>`: The directory where the filesystem will be mounted (e.g., `/mnt/data`).
    * `<type>`: The filesystem type (e.g., `ext4`, `ntfs`, `vfat`).
    * `<options>`: Mount options (e.g., `defaults`, `ro`, `noexec`).
    * `<dump>`: Used by the `dump` utility for backups (usually `0`).
    * `<pass>`: Order for filesystem checks during boot (root filesystem is usually `1`, others `2`, `0` to skip).
3.  **Example `/etc/fstab` entry:**
    ```
    /dev/sdb1 /mnt/data ext4 defaults 0 2
    ```
4.  **To check the `/etc/fstab` configuration without rebooting:**
    ```bash
    sudo mount -a
    ```
    * This command attempts to mount all filesystems listed in `/etc/fstab`.

### Checking type of Filesystem created on disk:
```bash
sudo blkid diskname(/dev/sdb1)
```
* This command displays information about the block device, including its UUID and filesystem type.
---
**Tools for Managing Block Devices:**
* **`lsblk`**: List block devices and their partitions in a tree-like format.
* **`fdisk` / `gdisk`**: Command-line tools for partitioning block devices.
* **`mkfs.<type>`**: Create a filesystem of a specific type on a block device (e.g., `mkfs.ext4`, `mkfs.vfat`).
* **`mount`**: Mount a filesystem to a specified mount point.
* **`umount`**: Unmount a mounted filesystem.
* **`df`**: Display disk space & mounts
* **`blkid`**: Print block device attributes (UUID, filesystem type, etc.).
---
**Block Storage Devices:**
* **DAS (Direct Attached Storage):** Storage directly connected to a host (e.g., internal hard drives, external USB drives).
* **SAN (Storage Area Network):** A dedicated high-speed network that provides block-level storage access to multiple servers.
    * Storage is often from a pool of storage.
    * Presents storage as logical units (LUNs).
    * Accesses storage in ranges of blocks.
    * LUNs are allocated to hosts as logical disks.

**File Storage Devices:**
* **NAS (Network Attached Storage):** File-based storage accessed over a network (e.g., using NFS or SMB/CIFS).

**NFS (Network File System):**

* A network protocol that allows you to share directories and files over a network.
*  Saves data in the form of files (as opposed to block-level access).
*  Exporting -term for directory sharing(making a local directory available to remote clients).
* `/etc/exports` (defines which directories are shared and which clients can access them, along with access permissions).
