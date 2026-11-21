# Day 10 - File Permissions & File Operations
## Objective
Learn Linux file operations and understand file permissions using chmod.

## Tasks Completed

### 1. File Creation
- Created devops.txt using touch.
- Created notes.txt and added content using echo.
- Created script.sh using vim.

### 2. File Reading
- Read notes.txt using cat.
- Viewed script.sh using vim -R.
- Used head -n 5 /etc/passwd.
- Used tail -n 5 /etc/passwd.

### 3. Permission Management
- Used ls -l to inspect file permissions.
- Made script.sh executable using chmod +x.
- Executed script.sh successfully.
- Set devops.txt permission to 444 (read-only).
- Set notes.txt permission to 640.
- Created project directory with permission 755.

### 4. Permission Testing
- Created test.sh and removed its execute permission using chmod 644.
- Attempted to execute test.sh and received Permission denied.
- Tested writing to a read-only file as student1 and received Permission denied.

Note: The first write test as root succeeded because root can bypass normal file permission restrictions. A separate test using student1 confirmed read-only protection.

## Final Permissions

| File/Directory | Permission | Meaning |
|---|---|---|
| devops.txt | 444 | Read-only |
| notes.txt | 640 | Owner: Read/Write, Group: Read |
| project/ | 755 | Owner: Full, Others: Read/Execute |
| script.sh | 755 | Executable |

## Key Learnings
- Linux permissions use Read (r), Write (w), and Execute (x).
- chmod is used to modify permissions.
- ls -l displays file permissions.
- File permissions help control access to files and directories.