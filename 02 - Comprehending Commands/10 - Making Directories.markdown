# **Creating Directories with mkdir in Linux**

In Linux, you can organize files by creating directories (folders) using the `mkdir` (make directory) command. Once created, directories can hold files or other directories, helping you keep your filesystem tidy. This note explains how to use `mkdir` for beginners, with practical examples using standard Linux directories like `/tmp` and `/home/user` that you can try on any system.

---

### **What is mkdir?**

- `mkdir` creates new, empty directories at the paths you specify.
- You can then use `cd` to enter them, `touch` to add files, or `mkdir` to add subdirectories.
- Example: `mkdir /tmp/mydir` creates a directory named `mydir` in `/tmp`.

---

# **Creating a Single Directory**

Use `mkdir` followed by a directory path to create one directory.

### **How It Works**

- Specify the directory’s name with an absolute (e.g., `/tmp/newdir`) or relative path (e.g., `newdir`).
- `mkdir` creates the directory; check with `ls`.
- Example: Create a directory in `/tmp`.
    
    ```bash
    cd /tmp
    mkdir mydir
    ls
    ```
    
    **Output:**
    
    ```
    mydir
    ```
    

### **Key Points**

- The directory is empty until you add files or subdirectories.
- You need write permission in the parent directory (e.g., `/tmp`).
- If the directory already exists, `mkdir` reports “File exists.”

### **Example**

- Create a directory in home:
    
    ```bash
    mkdir ~/myfolder
    ls ~
    ```
    
    **Output:**
    
    ```
    myfolder
    ```
    

---

# **Creating Multiple Directories**

You can create several directories at once by listing them with `mkdir`.

### **How It Works**

- Pass multiple directory names to `mkdir`, separated by spaces.
- Each directory is created independently.
- Example: Create two directories in `/tmp`.
    
    ```bash
    cd /tmp
    mkdir dir1 dir2
    ls
    ```
    
    **Output:**
    
    ```
    dir1  dir2
    ```
    

### **Key Points**

- Use absolute or relative paths; mix them if needed.
- Check with `ls` to confirm all directories were created.
- Avoid duplicate names to prevent “File exists” errors.

### **Example**

- Create directories in home:
    
    ```bash
    mkdir ~/work ~/play
    ls ~
    ```
    
    **Output:**
    
    ```
    play  work
    ```
    

---

# **Creating Nested Directories**

Use `mkdir -p` to create directories with subdirectories in one command.

### **How It Works**

- Without `p`, `mkdir` fails if parent directories don’t exist.
- With `p`, `mkdir` creates all necessary parent directories.
- Example: Create a deep directory structure in `/tmp`.
    
    ```bash
    mkdir -p /tmp/parent/child/grandchild
    ls /tmp/parent/child
    ```
    
    **Output:**
    
    ```
    grandchild
    ```
    

### **Key Points**

- `p` is great for nested paths like `/tmp/a/b/c`.
- Regular `mkdir` is fine for single-level directories.
- Use `ls` or `cd` to explore the new structure.

### **Example**

- Create a nested directory in home:
    
    ```bash
    mkdir -p ~/docs/projects/2023
    ls ~/docs/projects
    ```
    
    **Output:**
    
    ```
    2023
    ```
    

---

# **Adding Files to Directories**

After creating a directory, you can add files using `touch` or other commands.

### **How It Works**

- Use `cd` to enter the directory, then `touch` to create files.
- Verify with `ls` to see the contents.
- Example: Create a directory and file in `/tmp`.
    
    ```bash
    cd /tmp
    mkdir myproject
    touch /tmp/myproject/note.txt
    ls /tmp/myproject
    ```
    
    **Output:**
    
    ```
    note.txt
    ```
    

### **Key Points**

- Directories organize files; create as many as needed.
- Use absolute paths for precision or relative paths for convenience.
- Ensure you have permission to write in the directory.

### **Example**

- Create a directory and file in home:
    
    ```bash
    mkdir ~/school
    touch ~/school/homework
    ls ~/school
    ```
    
    **Output:**
    
    ```
    homework
    ```
    

---

### **Common Examples**

- **Create a directory in /tmp:**
    
    ```bash
    mkdir /tmp/test
    ls /tmp
    ```
    
    **Output:**
    
    ```
    test
    ```
    
- **Make multiple directories:**
    
    ```bash
    mkdir /tmp/alpha /tmp/beta
    ls /tmp
    ```
    
    **Output:**
    
    ```
    alpha  beta
    ```
    
- **Create a nested structure with a file:**
    
    ```bash
    mkdir -p /tmp/data/logs
    touch /tmp/data/logs/error.log
    ls /tmp/data/logs
    ```
    
    **Output:**
    
    ```
    error.log
    ```
    

---

### **Tips**

- **Check Creation:** Use `ls` to confirm directories and files exist.
- **Case Sensitivity:** `MyDir` and `mydir` are different.
- **Errors:** “Permission denied” means use `/tmp` or `~/`; “File exists” means pick a new name.
- **Practice:** Create directories in `/tmp` (e.g., `mkdir /tmp/test`) and add files with `touch`.
- **Use -p for Nesting:** Always use `mkdir -p` for deep paths to avoid errors.
- **Safe Spaces:** Stick to `/tmp` or `/home/user` for experiments.
- **Clean Up:** Remove directories later with `rm -r` (we’ll cover this soon).