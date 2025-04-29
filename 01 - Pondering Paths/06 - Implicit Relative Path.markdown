# **Running Programs with Explicit Relative Paths Using . in Linux**

In Linux, you can’t just type a program’s name like `run` to execute it in your current directory, even if it’s there. This is a safety feature to prevent accidentally running programs that might have the same names as system commands. Instead, you need to use an **explicit relative path** with `.` (the current directory) to tell Linux exactly where to look. This note explains how to run programs using `./`, with practical examples using standard Linux directories like `/bin` and `/tmp` that you can try on any system.

---

### **Why Can’t You Use Naked Paths?**

- A **naked path** is just a program name (e.g., `ls`) without a path like `/` or `./`.
- Linux doesn’t automatically check your **current working directory** (CWD) for naked paths to avoid running unintended programs.
- Example: Typing `cat` runs `/bin/cat`, not `cat` in your CWD, for safety.

---

# **Running Programs with ./**

Use `./program` to explicitly run a program in your current directory.

### **How It Works**

- `./` tells the shell to look for the program in the CWD.
- Without `./`, Linux checks system directories like `/bin` or `/usr/bin`, ignoring your CWD.
- Example: From `/bin`, run `ls` with `./`.
    
    ```bash
    cd /bin
    pwd
    ./ls
    ```
    
    **Output:**
    
    ```
    /bin
    cat  ls  pwd
    ```
    

### **Key Points**

- Always use `./` for programs in your CWD.
- Check your CWD with `pwd` to ensure you’re in the right place.
- If you see “command not found,” you likely forgot `./`.

### **Example**

- Run `cat` explicitly from `/bin`:
    
    ```bash
    cd /bin
    ./cat /etc/hostname
    ```
    
    **Output:**
    
    ```
    mylinux
    ```
    

---

# **When to Use ./**

You need `./` when a program isn’t in Linux’s default search paths (like `/bin`).

### **How It Works**

- Linux uses a `PATH` variable to find commands, but it skips the CWD for security.
- `./program` bypasses this, running the program where you are.
- Example: Create and run a script in `/tmp`.
    
    ```bash
    cd /tmp
    echo "echo hello" > myscript.sh
    chmod +x myscript.sh
    ./myscript.sh
    ```
    
    **Output:**
    
    ```
    hello
    ```
    

### **Key Points**

- Use `ls` to confirm the program exists in your CWD.
- Programs must be executable (use `chmod +x` if needed).
- `./` is common for scripts or custom programs.

### **Example**

- Run a command from `/usr/bin`:
    
    ```bash
    cd /usr/bin
    ./whoami
    ```
    
    **Output:**
    
    ```
    user
    ```
    

---

# **Combining ./ with Navigation**

You can use `./` with subdirectories or multiple dots in relative paths.

### **How It Works**

- Paths like `./dir/program` or `././program` work if they point to the program.
- Example: Run a program in a subdirectory of `/tmp`.
    
    ```bash
    mkdir -p /tmp/test
    cd /tmp
    echo "echo test" > test/run.sh
    chmod +x test/run.sh
    ./test/run.sh
    ```
    
    **Output:**
    
    ```
    test
    ```
    

### **Key Points**

- `./` anchors the path to your CWD, then follows subdirectories.
- Extra `./` (e.g., `././program`) is redundant but valid.
- Always verify paths with `ls` or `pwd`.

### **Example**

- Run `pwd` with dots from `/bin`:
    
    ```bash
    cd /bin
    ././pwd
    ```
    
    **Output:**
    
    ```
    /bin
    ```
    

---

### **Common Examples**

- **Run ls explicitly from /bin:**
    
    ```bash
    cd /bin
    ./ls
    ```
    
    **Output:**
    
    ```
    cat  ls  pwd
    ```
    
- **Execute a script in /tmp:**
    
    ```bash
    cd /tmp
    echo "date" > myscript.sh
    chmod +x myscript.sh
    ./myscript.sh
    ```
    
    **Output:**
    
    ```
    Tue Apr 15 12:34:56 UTC 2025
    ```
    
- **Run echo from /bin:**
    
    ```bash
    cd /bin
    ./echo hi
    ```
    
    **Output:**
    
    ```
    hi
    ```
    

---

### **Tips**

- **Use ./ Always:** For programs in your CWD, `./` is mandatory.
- **Check CWD:** Run `pwd` to ensure you’re in the right directory.
- **List Files:** Use `ls` to see programs you can run with `./`.
- **Case Sensitivity:** `./LS` and `./ls` are different.
- **Errors:** “Command not found” means you need `./`; “Permission denied” means `chmod +x`.
- **Practice:** Create scripts in `/tmp` (e.g., `echo hi > test.sh`) and run with `./test.sh`.
- **Stay Safe:** Only run `./` on programs you trust in your CWD.