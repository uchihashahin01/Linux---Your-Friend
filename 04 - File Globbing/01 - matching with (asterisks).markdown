# **Using Wildcard Globbing with * in Linux**

In Linux, the shell expands special patterns in commands, a process called **globbing**. The `*` wildcard is one of the most common glob patterns, matching any sequence of characters in filenames (except `/` or leading `.`). This lets you work with multiple files at once without typing each name. This note explains how to use `*` globbing for beginners, with practical examples using standard Linux directories like `/tmp` and `/home/user` that you can try on any system.

---

### **What is Globbing with *?**

- The `*` wildcard matches **zero or more characters** in a filename, excluding `/` (directory separator) and leading `.` (hidden files).
- The shell replaces `*` with all matching files before running the command.
- Example: `ls file_*` lists all files starting with `file_`, like `file_a`, `file_b`.

---

# **Matching Multiple Files with ***

Use `*` in a command to act on all files that match the pattern.

### **How It Works**

- Include `*` in a filename pattern (e.g., `prefix*` or `*suffix`).

- The shell expands it to all matching files in the current directory.

- Example: List files starting with `data_` in `/tmp`.

  ```bash
  cd /tmp
  touch data_1.txt data_2.txt data_3.txt
  ls data_*
  ```

  **Output:**

  ```
  data_1.txt  data_2.txt  data_3.txt
  ```

### **Key Points**

- `*` matches any characters except `/` or leading `.` (use `.*` for hidden files).
- The command runs on each matched file, like writing `ls data_1.txt data_2.txt`.
- Check matches with `echo pattern` to preview before running destructive commands.

### **Example**

- Echo files ending with `.txt`:

  ```bash
  cd /tmp
  touch note.txt memo.txt
  echo *.txt
  ```

  **Output:**

  ```
  memo.txt  note.txt
  ```

---

# **Matching a Single File with ***

If only one file matches, `*` expands to just that file.

### **How It Works**

- The `*` pattern can match exactly one file if that’s all that fits.

- The command treats it like you typed the full filename.

- Example: Match a single file in `/tmp`.

  ```bash
  cd /tmp
  touch single.txt
  rm other*.txt
  ls *.txt
  ```

  **Output:**

  ```
  single.txt
  ```

### **Key Points**

- The shell doesn’t care if one or many files match; it expands to whatever fits.
- Use `ls` to verify what exists before globbing.
- Patterns are case-sensitive (`File*` ≠ `file*`).

### **Example**

- Cat a single matching file:

  ```bash
  echo "hi" > /tmp/only.txt
  cat *.txt
  ```

  **Output:**

  ```
  hi
  ```

---

# **No Matches with ***

When no files match, the shell leaves the `*` pattern unchanged by default.

### **How It Works**

- If the pattern doesn’t match any files, the command sees the literal pattern (e.g., `nope*`).

- This avoids errors but may confuse commands expecting files.

- Example: Try a non-existent pattern.

  ```bash
  cd /tmp
  rm *.txt
  ls missing_*
  ```

  **Output:**

  ```
  ls: cannot access 'missing_*': No such file or directory
  ```

### **Key Points**

- Use `echo pattern` to test if a pattern matches before running critical commands.
- No matches often mean a typo or empty directory; check with `ls`.
- Some shells can be configured to error on no matches, but Bash keeps it literal.

### **Example**

- Echo a failed pattern:

  ```bash
  cd /tmp
  echo gone_*
  ```

  **Output:**

  ```
  gone_*
  ```

---

# **Using * in Paths**

The `*` wildcard can match parts of directory paths, but it won’t cross `/`.

### **How It Works**

- Use `*` within path segments (e.g., `/dir*/file`) to match directories or files.

- It matches names in that directory level, not deeper unless combined.

- Example: Match a directory in `/`.

  ```bash
  echo /ho*/*er
  ```

  **Output:**

  ```
  /home/user
  ```

### **Key Points**

- `*` doesn’t match `/`, so `/a/*/b` matches `/a/dir/b`, not `/a/dir/sub/b`.
- Avoid leading `.` in names unless using `.*` explicitly.
- Test complex patterns with `echo` to avoid unintended matches.

### **Example**

- List files in a matched directory:

  ```bash
  mkdir /tmp/test_dir
  touch /tmp/test_dir/file
  ls /tmp/test_*
  ```

  **Output:**

  ```
  /tmp/test_dir:
  file
  ```

---

### **Common Examples**

- **List all files:**

  ```bash
  cd /tmp
  touch a.txt b.txt
  ls *
  ```

  **Output:**

  ```
  a.txt  b.txt
  ```

- **Remove files with a prefix:**

  ```bash
  cd /tmp
  touch old_1 old_2
  rm old_*
  ls
  ```

  **Output:**

  ```
  (nothing)
  ```

- **Match a directory path:**

  ```bash
  echo /et*/hos*
  ```

  **Output:**

  ```
  /etc/hosts
  ```

---

### **Tips**

- **Preview Matches:** Use `echo pattern` to see what `*` will expand to before running commands.
- **Case Sensitivity:** `File*` ≠ `file*`; match exactly or test both.
- **Errors:** “No such file” often means no matches; verify with `ls`.
- **Practice:** Create files in `/tmp` (e.g., `touch /tmp/test_1`) and try `ls test_*`.
- **Avoid Hidden Files:** `*` skips files starting with `.`; use `.*` for those.
- **Safe Testing:** Experiment in `/tmp` or `/home/user` to avoid system files.
- **Limit Scope:** Use `*` in specific directories (e.g., `/tmp/*`) to avoid broad matches.

---

### **Solving the Challenge**

You need to change to the `/challenge` directory from your home directory (`~`) using a glob pattern with `cd` that’s at most four characters long, then run `/challenge/run` to get the flag.

1. **Understand the constraint:**

   - From `~`, run `cd pattern` where `pattern` is ≤ 4 characters and uses `*` to match `/challenge`.
   - The pattern must expand to `/challenge` when globbed.

2. **Test glob patterns:**

   - The directory `/challenge` exists at the root level (`/`).
   - A pattern like `/*` matches all top-level directories, including `/challenge`, but it’s too broad and may match multiple paths.
   - Try a pattern starting with `/c*`:
     - `/c*` is four characters (`/`, `c`, `*`).
     - In Bash, `/c*` expands to all root-level directories starting with `c`, like `/challenge`.

   ```bash
   echo /c*
   ```

   **Output (hypothetical)**:

   ```
   /challenge
   ```

   If `/challenge` is the only match, `/c*` works. If other directories like `/config` exist, `/c*` might expand to multiple paths, causing `cd /c*` to fail (since `cd` takes one argument).

3. **Use a precise pattern:**

   - To ensure a single match, refine the pattern. Since `/challenge` is the target, `/c*` is likely correct if `/challenge` is the only `c`-starting directory at `/`.
   - Test in home:

     ```bash
     cd ~
     cd /c*
     pwd
     ```

     **Output**:

     ```
     /challenge
     ```

4. **Run the command:**

   Once in `/challenge`:

   ```bash
   /challenge/run
   ```

   This should print the flag.

### **Key Notes**

- **Four Characters:** The pattern must be exactly `/c*` (4 chars: `/`, `c`, `*`) to match `/challenge`.
- **Single Match:** If `/c*` matches multiple directories (e.g., `/config`, `/challenge`), `cd /c*` fails. The challenge implies `/challenge` is the only match.
- **Verify Directory:** Use `echo /c*` to confirm it expands to `/challenge` only.
- **Practice:** In `/tmp`, create `test_dir` and try `cd /tmp/t*` to understand globbing.
- **Safe Run:** Work from `~` and only run `/challenge/run` in `/challenge`.

If `/c*` doesn’t work or matches too many paths, let me know, and I’ll help refine the pattern!