### Disk Usage :
du - View the size of a file or a directory:
-  h : print size in human-readable format. eg 98 MB 
-  s : Displays only the total size for each file/directory
-  a (all): Displays the sizes of all files, including those in subdirectories. 
-  c (total): Displays a total count of all files and directories. 
-  r (recursive): Used when you want to include all subdirectories. 
-  ls -lh :  also prints size of file
---

### Archiving Files:
Using `tar`: 
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
#### Compression Tools:
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

## Search Files and Directories:
#### **locate:** 
`locate filename` (depends on mlocate.db).If new installation of linux, may need to run sudo updatedb command as root user.

#### **find:** 
Find files or directories.
```
 `find path/to/dir -name *.txt` Find text files in a specific dirctory.
 `find -type f`  Find only files
 `find -perm 777 -type f` Findfiles with specific permissions. 
 ```
#### Find and read Large Files
1. **`head` Command**:
   - Displays the first `n` lines of a file.
   - Example:
     ```
     head -n 10 file.txt
     ```
2. **`tail` Command**:
   - Displays the last `n` lines of a file.
   - Example:
     ```
     tail -n 10 file.txt
     ```
3. **`less` Command**:
   - Displays file content in a paginated format for easier reading.
   - Syntax:
     ```
     less filename
     ```
   **Key Bindings in `less`:**
   - `Space`: Move forward to the next page.
   - `b`: Move backward to the previous page.
   - `q`: Quit the `less` viewer.
4. **`more` Command**:
   - Similar to `less`, but with fewer features.
   - Syntax:
     ```
     more filename
     ```

#### **Basics of `grep`:**
 `grep` is used to locate text patterns within files or directories.

**General Syntax**:  
  ```
  grep [options] 'pattern' file(s)
  ```
#### **Common Commands and Options:**

1. **Simple Search**  
   ```
   grep 'pattern' file.txt
   ```
   - Searches for the specified pattern in `file.txt`.

2. **Case-Insensitive Search**  
   ```
   grep -i 'pattern' file.txt
   ```
   - Ignores case sensitivity while searching.

3. **Recursive Search**  
   ```
   grep -r 'pattern' directory/
   ```
   - Searches for the pattern within all files in a directory and its subdirectories.

4. **Show Line Numbers**  
   ```
   grep -n 'pattern' file.txt
   ```
   - Displays line numbers where the pattern occurs.

5. **Count Matching Lines**  
   ```
   grep -c 'pattern' file.txt
   ```
   - Counts and displays the number of lines that match the pattern.

6. **Match Whole Words Only**  
   ```
   grep -w 'word' file.txt
   ```
   - Matches whole words (not substrings) within the file.

7. **Invert Match**  
   ```
   grep -v 'pattern' file.txt
   ```
   - Displays lines that **do not** contain the pattern.

8. **Search with Context**  
   ```
   grep -A N 'pattern' file.txt  # Show N lines after a match
   grep -B N 'pattern' file.txt  # Show N lines before a match
   grep -C N 'pattern' file.txt  # Show N lines around a match
   ```
9. **Search Across Multiple Files**  
   ```
   grep 'pattern' file1.txt file2.txt
   ```

10. **Other Uses:**
- $env | grep -i user
-  ls some/dir | grep '.txt'
-  cat file.txt | grep 'pattern'
---
#### **`tee` Command**
Duplicate o/p to file and screen simultaneously.
- **General Syntax**:  
 ```
  command | tee filename
```
- **Examples**: 
 ```
 echo $SHELL | tee shell.txt  (overwrites)
 echo $SHELL | tee -a shell.txt (appends)
 ```
---
### **Read Binary Files using `Strings`**  
```
`strings` path/to/dir binaryfile | grep 'pattern'
```
---
#### **Special File: `/dev/null`**
- **Definition**: A special file that discards any data written to it.
- **Usage**:
  ```
  command > /dev/null
  ```
  - Redirects command output to `/dev/null`, effectively silencing it.
