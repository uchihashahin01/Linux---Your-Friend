# **Using Relative Paths in Linux**

In Linux, you can specify file or program locations using **absolute paths** (starting with `/`) or **relative paths** (based on your current location). Relative paths don’t start with `/` and depend on your **current working directory**—the directory your terminal is in. This makes them flexible but context-dependent. This note explains relative paths for beginners, with practical examples using standard Linux directories like `/tmp` and `/etc` that you can try on any system.

---

### **What is a Relative Path?**

- A **relative path** describes a file or program’s location starting from your **current working directory** (CWD).
- Unlike absolute paths (e.g., `/bin/ls`), relative paths don’t start with `/`.
- Example: If you’re in `/usr` and want `/usr/bin/ls`, the relative path is `bin/ls`.

---

# **How Relative Paths Work**

Use a relative path to run a program or access a file based on where you are.

### **How It Works**

- The shell interprets the path relative to your CWD, shown by `pwd` or your prompt.

- Example: From `/`, the relative path to `/bin/ls` is `bin/ls`.

- Run the program by typing its relative path.

  ```bash
  cd /
  pwd
  bin/ls
  ```

  **Output:**

  ```
  / 
  cat  ls  pwd
  ```

### **Key Points**

- Use `pwd` to check your CWD before using relative paths.
- Relative paths change depending on your location.
- If the path is wrong, you’ll get “No such file or directory.”

### **Example**

- Run `cat` from `/`:

  ```bash
  cd /
  bin/cat /etc/hostname
  ```

  **Output:**

  ```
  mylinux
  ```

---

# **Navigating with Relative Paths**

Relative paths often use `..` to move up directories or subdirectories to go deeper.

### **How It Works**

- `..` means “parent directory” (one level up).

- Combine subdirectories and `..` to reach your target.

- Example: From `/tmp/a/b/c`, the relative path to `/tmp/a/b/file.txt` is `../file.txt`.

  ```bash
  mkdir -p /tmp/a/b/c
  cd /tmp/a/b/c
  pwd
  touch /tmp/a/b/file.txt
  ls ../file.txt
  ```

  **Output:**

  ```
  /tmp/a/b/c
  ../file.txt
  ```

### **Key Points**

- Use `ls` to see what’s in your CWD or subdirectories.
- Count `..` steps to move up multiple levels (e.g., `../../file`).
- Relative paths are shorter than absolute paths but need the right CWD.

### **Example**

- Access a file from `/usr/bin`:

  ```bash
  cd /usr/bin
  pwd
  cd ..
  ls share
  ```

  **Output:**

  ```
  /usr/bin
  doc  locale
  ```

---

# **Relative Paths in Action**

The same file or program has different relative paths depending on your CWD.

### **How It Works**

- Example: To reach `/etc/hosts`:

  - From `/`: Relative path is `etc/hosts`.
  - From `/tmp`: Relative path is `../etc/hosts`.
  - From `/etc/passwd`: Relative path is `../hosts`.

- Run or access it from the right directory.

  ```bash
  cd /
  cat etc/hosts
  ```

  **Output:**

  ```
  127.0.0.1 localhost
  ```

### **Key Points**

- Always know your CWD (use `pwd`) to craft the correct relative path.
- Test paths with `ls` to avoid errors.
- Relative paths save typing when you’re close to the target.

### **Example**

- Run `whoami` from `/`:

  ```bash
  cd /
  usr/bin/whoami
  ```

  **Output:**

  ```
  user
  ```

---

### **Common Examples**

- **List /bin from /:**

  ```bash
  cd /
  bin/ls
  ```

  **Output:**

  ```
  cat  ls  pwd
  ```

- **View a file from /tmp:**

  ```bash
  cd /tmp
  cat ../etc/hostname
  ```

  **Output:**

  ```
  mylinux
  ```

- **Move up and run a command:**

  ```bash
  cd /usr/bin
  ../bin/echo hi
  ```

  **Output:**

  ```
  hi
  ```

---

### **Tips**

- **Know Your CWD:** Use `pwd` or check your prompt to understand your starting point.
- **Explore First:** Run `ls` to see directories and files for relative paths.
- **Case Sensitivity:** `Bin/ls` won’t work; use `bin/ls`.
- **Error Fixes:** “No such file” means the relative path or CWD is wrong; adjust with `pwd` and `ls`.
- **Practice:** Try relative paths from `/`, `/tmp`, or `/home` to see how they change.
- **Use .. Wisely:** Count parent directories carefully (e.g., `../..` for two levels up).
- **Keep It Simple:** Start with small paths like `bin/cat` or `etc/hosts`.