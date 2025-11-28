# Bash/Linux Scripting Cheat Sheet (Assignment Edition)

---

## 1. **Script Setup & Making Scripts Executable**

| Command or Line           | What it Does                                         | Example/When to Use                         |
|--------------------------|------------------------------------------------------|---------------------------------------------|
| `#!/bin/bash`            | "Run this script using Bash shell" (at script top)   | Start every Bash script with this line      |
| `chmod +x script.sh`     | Makes a script file executable                       | After you write a script, before you run it |
| `./script.sh`            | Runs an executable script in current directory       | To launch your script from the terminal     |


---

## 2. **Navigation & Path Handling**

| Command                  | What it Does                   | Example/When to Use           |
|--------------------------|--------------------------------|-------------------------------|
| `cd /some/path`          | Change to directory            | Go where your files are       |
| `cd ..`                  | Go up one directory            | Exit/back-track in folders    |
| `pwd`                    | Show current directory         | Always know "where you are"   |
| `ls`                     | List files in directory        | See what's here               |

---

## 3. **Input Arguments & Checks**

| Command/Pattern           | What/Why/When                                | Example                          |
|---------------------------|----------------------------------------------|-----------------------------------|
| `$1`                      | The first input when running a script        | `./script.sh /my/folder`          |
| `[ -z "$1" ]`             | True if `$1` is empty                        | Check if an argument was passed   |
| `if [ -z "$1" ]; then ...`| Conditional: "Did user forget the argument?" |                                   |

---

## 4. **File & Directory Existence Checks**

| Command                    | What it Does                                       | Use When                      |
|----------------------------|----------------------------------------------------|-------------------------------|
| `[ -d folder ]`            | True if "folder" exists and is a directory         | Need to check for a folder    |
| `[ -f file.txt ]`          | True if "file.txt" exists and is a regular file    | Check before opening/using it |
| `if [ ! -f file ]; then...`| Runs if file does **not** exist                    | For safe error handling       |

---

## 5. **Extracting Archives**

| Command                                         | What it Does                                | When to Use                                            |
|-------------------------------------------------|---------------------------------------------|--------------------------------------------------------|
| `tar -xzf archive.tar.gz`                       | Extract `.tar.gz` files                     | Unpack many files/folders at once                      |
| `unzip myfile.zip`                              | Extract `.zip` archives                     | Extract a zipfile (make sure `unzip` is installed)     |

> **Flags for `tar`:**
> - `-x` = e**X**tract, `-z` = g**Z**ip compression, `-f` = use **F**ile specified

---

## 6. **Finding Files**

| Command                                              | What it Does                                        | Example Scenario                                  |
|------------------------------------------------------|-----------------------------------------------------|---------------------------------------------------|
| `find . -type f -name "*.txt"`                       | Find `.txt` files under current dir                 | List homework answers, log files, etc.            |
| `find foldername -type f -name "*.txt"`              | Find `.txt` files only inside `foldername`          | After extracting a project/archive                |

---

## 7. **System Info Commands (for Reports)**

| Command               | What it Shows                         | Assignment Usage                |
|-----------------------|---------------------------------------|---------------------------------|
| `date`                | Current date and time                 | Timestamp your output           |
| `top -b -n1 | grep "Cpu"` | Snapshot of current CPU usage       | In a summary report             |
| `free -h`             | RAM and swap memory usage             | Memory stats                    |
| `df -h`               | Disk space (human-readable units)     | Disk stats                      |
| `who`                 | Who is logged in                      | List users                      |
| `hostname`            | Computer (host) name                  | System header                   |
| `ip addr show`        | Network interfaces and IP addresses   | Network stats                   |

---

## 8. **Redirecting Output to Files**

| Command/Concept      | What it Does                                 | Example Usage                                    |
|----------------------|----------------------------------------------|--------------------------------------------------|
| `> filename`         | Redirects output to **overwrite** a file     | `echo "Hi" > myfile.txt`                         |
| `>> filename`        | Redirects output to **append** to a file     | `echo "Bye" >> myfile.txt`                       |
| `{ ... } > file`     | Everything inside `{}` gets written to file  | Used in scripts to generate reports              |

---

## 9. **Extra: Printing, Debugging, Blank Lines**

| Command/Pattern         | What it Does                | Example/When           |
|-------------------------|-----------------------------|------------------------|
| `echo "Some text"`      | Print a message or info     | Output values, status  |
| `echo`                  | Print a blank line          | For pretty output      |
| `echo $VARIABLE`        | Print value of variable     | Debug or display vars  |
| `echo "Error: ..." >&2` | Print error to stderr       | Good for real scripts  |

---

## 10. **General Script Structure Template**

```bash
#!/bin/bash
# INPUT CHECKS
if [ -z "$1" ]; then
  echo "Usage: $0 <directory>"
  exit 1
fi

# FILE/DIR CHECKS
if [ ! -d "$1" ]; then
  echo "Error: directory does not exist."
  exit 1
fi

# NAVIGATE & PROCESS
cd "$1"
if [ -f myarchive.tar.gz ]; then
  tar -xzf myarchive.tar.gz
fi

# FIND FILES
find . -type f -name "*.txt"
```

---

## "When, How, and Why" Mini-Guide

- Use `chmod +x script.sh` **after writing a script** so you can run it with `./script.sh`
- Use `cd ..` whenever you need to "go up one directory"
- Use `find` when you need to locate specific files across directories
- Use `tar` and `unzip` to unpack archives you download or are given
- Use `df`, `free`, `top | grep Cpu` for system/resource reporting
- Always **check if files or directories exist** before using them in scripts to avoid errors!

---

Keep this cheat sheet handy as a quick reference when you’re automating new tasks or reviewing previous work!