## File Compression and Archival

### Disk Usage  
du - View the size of a file or a directory:
-  du -sh : print size in human-readable format. eg 98 MB 
-  ls -lh :  also prints size of file
---

## Archiving Files

### Using `tar` 
- Used to archive data (group multiple files or directories into a single file).
- Create an archive:  
  ```bash
  tar -cf <file_name.tar> <files/directories>
  ```
  - tar -c : used to create archive
        -f : used to specify file name
- View contents of tar file:  
  ```bash
  tar -tf <file_name.tar>
  ```
- Extract contents of tar file:  
  ```bash
  tar -xf <file_name.tar>
  ```
- Compress archive:  
  ```bash
  tar -zcf <file_name.tar>  # -z to compress tar file
  ```

### Compression Tools
- **Compressing**:  
  - `bzip2`: Adds `.bz2` extension.  
  - `gzip`: Adds `.gz` extension.  
  - `xz`: Adds `.xz` extension.

- **Uncompressing**:  
  - `bunzip2`, `gunzip`, `unxz`.


- **View Compressed Files Without extracting**:
  ```bash
  bzcat /zcat/ xzcat
  ```
---
