### Types of Linux Shells
- **Most Common:** Bash Shell

---

### Commands and Their Usage

#### **1. `pwd`**
- Displays the current working directory.

#### **2. `ls`**
- Lists files and directories in the current directory.

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
    Example: `cp -r India/Ontario/City.txt Canada/Ontario/City.txt`

#### **8. `rm`**
- Removes files or directories.
- To remove directories, use the `-r` option.  
  Example: `rm -r directory_name`

---

### Notes
- **Root Directory:** `/`  
  Used as the base for absolute paths.
- **Relative Paths:** Paths relative to the current directory.
- **Recursive Copy:** Use `cp -r` to copy directories and their contents.

---

