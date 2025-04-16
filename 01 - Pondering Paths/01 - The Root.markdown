# **Running Programs with Absolute Paths in Linux**

The Linux filesystem starts at the root directory, `/`, which contains directories, configuration files, programs, and sometimes special files like flags. To run a program, you can use its **absolute path**—a full path starting from `/`—to tell the system exactly where to find it. This note explains how to invoke programs using absolute paths in a beginner-friendly way with examples and their outputs.

---

### **What is an Absolute Path?**

- An **absolute path** is the complete path to a file or program, starting from the root directory (`/`).
- Example: `/pwn` points to a program named `pwn` directly in `/`.
- Unlike relative paths (e.g., `./pwn`), absolute paths work from anywhere in the filesystem.

---

# **Running a Program with an Absolute Path**

To run a program, type its absolute path in the terminal and press Enter.

### **How It Works**

- The shell looks for the program at the exact location specified by the absolute path.
- If the program exists and is executable, it runs and produces output (like a flag).
- Example: `/pwn` runs the `pwn` program located in `/`.

    ```bash
    /pwn
    ```

    **Output:**
    ```
    pwn.college{A1B2C3D4E5F6G7H8I9J0}
    ```

### **Key Points**

- Absolute paths start with `/` and include every directory to the program.
- No need to be in the program’s directory to run it.
- Ensure the program is executable; if not, you’ll get an error.

### **Example**

- Run a program in `/bin`:

    ```bash
    /bin/ls
    ```

    **Output:**
    ```
    dir1  dir2  file.txt
    ```

---

# **Why Use Absolute Paths?**

Absolute paths are useful when you need to be specific about a program’s location.

### **How It Works**

- Guarantees the shell runs the exact program, no matter your current directory.
- Avoids confusion with programs of the same name in different locations.
- Example: Running `/challenge/run` ensures you execute that specific program.

    ```bash
    /challenge/run
    ```

    **Output:**
    ```
    Flag: pwn.college{X9Y8Z7W6V5U4T3S2R1Q0}
    ```

### **Key Points**

- Use absolute paths for clarity in scripts or challenges.
- Common for system programs (e.g., `/bin/cat`, `/usr/bin/echo`).
- Errors like “command not found” mean the path is wrong or the program doesn’t exist.

### **Example**

- Run a program in `/usr/bin`:

    ```bash
    /usr/bin/whoami
    ```

    **Output:**
    ```
    hacker
    ```

---

### **Common Examples**

- **Run a challenge program:**

    ```bash
    /challenge/pwn
    ```

    **Output:**
    ```
    pwn.college{K5L6M7N8O9P0Q1R2S3T4}
    ```

- **List files with a system tool:**

    ```bash
    /bin/ls /tmp
    ```

    **Output:**
    ```
    temp1  temp2
    ```

- **Check system info:**

    ```bash
    /bin/hostname
    ```

    **Output:**
    ```
    dojo
    ```

---

### **Tips**

- **Start with /:** Absolute paths always begin with the root directory.
- **Check Existence:** Use `ls /path` to confirm the program is there.
- **Case Sensitivity:** Paths like `/Pwn` and `/pwn` are different.
- **Errors:** If you see “permission denied,” the program may not be executable.
- **Practice:** Try running `/bin/echo` or `/bin/pwd` to see absolute paths in action.
- **Flags:** Some programs output flags directly; capture them for challenges.
- **No Spaces:** Ensure no extra spaces in the path (e.g., `/ pwn` won’t work).