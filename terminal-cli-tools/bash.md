---
description: Bourne Again SHell
---

# Bash







## Bash Scripting:

add to path:

```
export PATH=$PATH:/path/to/dir
```



cli argument parsing

```
$1
```



else set default value:

```
FIRST_OR_DEFAULT="${FIRST:-default_value_here}"
```



### Loops

```
for file in *.log; do
  echo "Processing $file"
done
```

### Functions&#x20;

```
greet() {
  local name=$1
  echo "Hello, $name!"
}
greet "Alice"
```



### Datatypes:

string, number, array, associative array (dict)

## Operators:

### Comparison Operators

* `-eq`: Equal to
* `-ne`: Not equal to
* `-lt`: Less than
* `-le`: Less than or equal to
* `-gt`: Greater than
* `-ge`: Greater than or equal to

***

### String Comparison Operators

* `=`: Equal to
* `!=`: Not equal to
* `<`: Less than, in ASCII alphabetical order
* `>`: Greater than, in ASCII alphabetical order

***

***

### Arithmetic Operators

* `+`: Addition
* `-`: Subtraction
* `*`: Multiplication
* `/`: Division
* `%`: Modulus (remainder of division)
* For exponentiation, use external tools like `bc` or `awk`.

***

### Logical Operators

* `&&`: Logical AND
* `||`: Logical OR
* `!`: Logical NOT

***

### File Test Operators

* `-e`: Checks if a file exists
* `-d`: Checks if a directory exists
* `-f`: Checks if a file is a regular file
* `-s`: Checks if a file is not empty

\
source: [https://www.w3schools.com/bash/bash\_operators.php](https://www.w3schools.com/bash/bash_operators.php)



***



```
trap
```



## Bash Keyboard shortcuts

* <kbd>Ctrl</kbd>+<kbd>e</kbd> – Move the cursor to the end of the current commandline





## Commands to use:



### Useful Commands:

```
history | grep apt
```







### Basic Commands:

| Command | Notes                                                         | Parameters                                                                                                                                                                                                                                            | Use Frequency          |
| ------- | ------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| mkdir   | can create multiple directories                               | <p><code>-p</code> - Create parent directories as needed</p><p><code>-v</code> - Show a message for each created directory</p><p><code>-m</code> - Set file mode (permissions)</p>                                                                    | often                  |
| rm      |                                                               | <p><code>-r</code> - Delete a folder and everything inside it</p><p><code>-i</code> - Ask before deleting each file</p><p><code>-f</code> - Force delete without asking</p><p><code>-v</code> - Verbose mode, show files being removed</p>            | often                  |
| cat     |                                                               | <p><code>-n</code> - Add numbers to each line</p><p><code>-b</code> - Add numbers only to lines with text</p><p><code>-s</code> - Remove extra empty lines</p><p><code>-v</code> - Show non-printing characters (except for tabs and end of line)</p> | commonly               |
| alias   | can create alias and also check what aliases are set          |                                                                                                                                                                                                                                                       | setup once occasionaly |
| man     | read manuals of clis                                          |                                                                                                                                                                                                                                                       | rarely                 |
| touch   | can create files but also update timestamps of existing files |                                                                                                                                                                                                                                                       | rare                   |
| ls      |                                                               |                                                                                                                                                                                                                                                       |                        |
| pwd     |                                                               |                                                                                                                                                                                                                                                       |                        |
| cd      |                                                               |                                                                                                                                                                                                                                                       |                        |
| echo    |                                                               |                                                                                                                                                                                                                                                       |                        |
| cp      |                                                               |                                                                                                                                                                                                                                                       |                        |
| mv      |                                                               |                                                                                                                                                                                                                                                       |                        |
|         |                                                               |                                                                                                                                                                                                                                                       |                        |

Bash Search Text (grep)\
Bash Pattern Scan (awk)\
Bash Stream Editor (sed)\
Bash Remove Section (cut)\
Bash Sort Lines (sort)\
Bash View End (tail)\
Bash View Start (head)

Bash Process Status (ps)\
Bash List Processes (top)\
Bash Disk Space (df)\
Bash Directory Usage (du)\
Bash Memory Usage (free)\
Bash Terminate (kill)\
Bash Uptime (uptime)

Bash Ping (ping)\
Bash URL Transfer (curl)\
Bash Downloader (wget)\
Bash Remote Connect (ssh)\
Bash Secure Copy (scp)\
Bash File Sync (rsync)

File Compression\
Bash Compress (zip)\
Bash Extract (unzip)\
Bash TAR Archive (tar)

File Permissions\
Bash Ownership \
Bash Modify (chmod)\
Bash Ownership (chown)\
Bash Group (chgrp)

Bash Schedule (cron)







#### crontab

* `-e`: Edit the crontab file for the current user.
* `-l`: List the crontab entries for the current user.
* `-r`: Remove the crontab file for the current user.

Setting Up Cron Jobs

Cron jobs are defined using a specific syntax in the crontab file. Each line in the file represents a task and follows this format:

```bash
* * * * * command_to_execute
```

* **Minute**: 0-59
* **Hour**: 0-23
* **Day of Month**: 1-31
* **Month**: 1-12
* **Day of Week**: 0-7 (0 and 7 are Sunday)

<br>

