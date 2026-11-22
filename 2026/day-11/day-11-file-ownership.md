# Day 11 – File Ownership Challenge (chown & chgrp)

## Objective

Learn how to view and manage Linux file and directory ownership using `ls -l`, `chown`, `chgrp`, and recursive ownership changes.

---

## Task 1: Understanding Ownership

### Commands Used

```bash
whoami
pwd
ls -l
ls -ld /root
```

### Observations

- Current user: `root`
- Current working directory: `/root`
- The `ls -l` command displays file permissions, owner, group, size, date, and filename.
- The `ls -ld /root` command displayed the ownership and permissions of the root directory.
- The `/root` directory was owned by `root:root`.
- File owner represents the user who owns the file, while group represents the group associated with it.

**Output Format:**

```text
-rw-r--r-- 1 owner group size date filename
```

---

## Task 2: Basic chown Operations

Created `devops-file.txt` and changed its ownership from `root` to `tokyo`, then to `berlin`.

### Commands Used

```bash
touch devops-file.txt

useradd tokyo
id tokyo

chown tokyo devops-file.txt
ls -l devops-file.txt

useradd berlin
id berlin

chown berlin devops-file.txt
ls -l devops-file.txt
```

### Results

- Created file: `devops-file.txt`
- Initial owner: `root`
- First owner: `tokyo`
- Final owner: `berlin`
- Group remained: `root`

**Final Ownership:**

```text
berlin:root
```

---

## Task 3: Basic chgrp Operations

Created `team-notes.txt`, created the `heist-team` group, and changed the file's group ownership.

### Commands Used

```bash
touch team-notes.txt

groupadd heist-team
getent group heist-team

chgrp heist-team team-notes.txt
ls -l team-notes.txt
```

### Results

- Created file: `team-notes.txt`
- Created group: `heist-team`
- Initial ownership: `root:root`
- Final ownership: `root:heist-team`

The `chgrp` command successfully changed the group ownership.

---

## Task 4: Combined Owner & Group Change

Created `project-config.yaml` and changed both its owner and group using `chown`.

Also created the `app-logs` directory and assigned ownership to `berlin:heist-team`.

### Commands Used

```bash
touch project-config.yaml

useradd professor
id professor

chown professor:heist-team project-config.yaml
ls -l project-config.yaml

mkdir app-logs

chown berlin:heist-team app-logs
ls -ld app-logs
```

### Results

| File / Directory | Owner | Group |
|---|---|---|
| project-config.yaml | professor | heist-team |
| app-logs/ | berlin | heist-team |

Both owner and group changes were verified successfully.

---

## Task 5: Recursive Ownership

Created the `heist-project` directory structure with two subdirectories and files.

Changed ownership of the complete directory structure using the recursive `-R` option.

### Commands Used

```bash
mkdir -p heist-project/vault
mkdir -p heist-project/plans

touch heist-project/vault/gold.txt
touch heist-project/plans/strategy.conf

ls -lR heist-project/

groupadd planners
getent group planners

chown -R professor:planners heist-project/

ls -lR heist-project/
ls -ld heist-project
```

### Results

The recursive ownership change was successful.

| File / Directory | Owner | Group |
|---|---|---|
| heist-project/ | professor | planners |
| vault/ | professor | planners |
| plans/ | professor | planners |
| gold.txt | professor | planners |
| strategy.conf | professor | planners |

The `-R` option changed ownership recursively for the parent directory, subdirectories, and files.

---

## Task 6: Practice Challenge

Created three users, two groups, one directory, and three files.

Assigned different users and groups to each file.

### Commands Used

```bash
useradd nairobi

id tokyo
id berlin
id nairobi

groupadd vault-team
groupadd tech-team

mkdir bank-heist

touch bank-heist/access-codes.txt
touch bank-heist/blueprints.pdf
touch bank-heist/escape-plan.txt

chown tokyo:vault-team bank-heist/access-codes.txt

chown berlin:tech-team bank-heist/blueprints.pdf

chown nairobi:vault-team bank-heist/escape-plan.txt

ls -l bank-heist/
```

### Final Ownership Results

| File | Owner | Group |
|---|---|---|
| access-codes.txt | tokyo | vault-team |
| blueprints.pdf | berlin | tech-team |
| escape-plan.txt | nairobi | vault-team |

### Final Terminal Output

```text
-rw-r--r-- 1 tokyo   vault-team 0 access-codes.txt
-rw-r--r-- 1 berlin  tech-team  0 blueprints.pdf
-rw-r--r-- 1 nairobi vault-team 0 escape-plan.txt
```

All three file ownership assignments were successfully verified using `ls -l bank-heist/`.

---

## Key Commands Learned

```bash
# View file ownership
ls -l filename

# View directory ownership
ls -ld directory

# Change file owner
chown newowner filename

# Change group ownership
chgrp newgroup filename

# Change both owner and group
chown owner:group filename

# Change ownership recursively
chown -R owner:group directory/
```

---

## What I Learned

1. How to identify file owners and groups using `ls -l`.
2. How to change file ownership using `chown` and group ownership using `chgrp`.
3. How to assign both owner and group using `chown owner:group`.
4. How to apply recursive ownership changes using `chown -R`.
5. How to create Linux users and groups and assign file ownership.
6. How to verify ownership changes using `ls -l` and `ls -ld`.

---

## Why File Ownership Matters in DevOps

File ownership is important in real-world DevOps environments for:

- Application deployments
- Shared team directories
- Container file permissions
- CI/CD pipeline artifacts
- Log file management
- Access control and security

---

## Screenshots

Terminal screenshots captured during the practical tasks are available in the `screenshots/` folder.

---

## Conclusion

Successfully completed all six tasks of the Day 11 File Ownership Challenge.

Practiced Linux file and directory ownership management using `chown`, `chgrp`, and recursive ownership changes.

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham
