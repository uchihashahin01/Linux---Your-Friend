# Grep Cheatsheet: Your Quick Guide to Searching Files! 🚀

**Grep** is your go-to command for finding lines in files that match a specific string or pattern. It’s fast, flexible, and a must-know for anyone working in the terminal. Let’s dive into the essentials!

## Basic Syntax
```bash
grep SEARCH_STRING /path/to/file
```

## 🎯 Common Examples

### 1. Search for a Word
Find all lines containing a specific word in a file.
```bash
grep apple fruits.txt
```
**Output**: Lines in `fruits.txt` with "apple".

### 2. Search Multiple Files
Look for a string across multiple files at once.
```bash
grep hello *.txt
```
**Output**: Matches from all `.txt` files in the current directory.

### 3. Case-Insensitive Search
Ignore case (e.g., match "Apple", "APPLE", or "aPpLe") with `-i`.
```bash
grep -i Apple fruits.txt
```

### 4. Show Line Numbers
Pinpoint matches with line numbers using `-n`.
```bash
grep -n error log.txt
```
**Output**: Matching lines from `log.txt` with line numbers.

### 5. Search Recursively
Hunt for a string in all files within a directory using `-r`.
```bash
grep -r TODO /project
```
**Output**: Matches from all files in `/project`.

## 💡 Pro Tips
- **Spaces in strings?** Wrap them in quotes:  
  ```bash
  grep "error code" file.txt
  ```
- **Need the full file?** Grep only shows matches—use `cat` to see everything.
- **Mix and match flags** like `-i`, `-n`, or `-r` for power searches!

---

Happy grepping! 🔍 Share this cheatsheet and star the repo if it helped! 😄