# Linux Lab – Managing File Permissions

## Objective

In this lab you've learnd how to manage Linux file permissions and update a company folder structure.

### Goals

* Change folder and file permissions to match the appropriate group structure
* Modify file permissions for a specific user
* Update the company folder structure

---

# Initial Folder Structure

```
/home/ec2-user/CompanyA/
├── Employees/
├── Finance/
├── HR/
├── IA/
├── Management/
└── SharedFolders/
```

Each department folder contains files used by different teams.

---

# Task 1 – Check Current Permissions

Display the current permissions of all folders.

```bash
ls -l /home/ec2-user
```

To view permissions recursively:

```bash
ls -lR CompanyA
```

Example output:

```
drwxr-xr-x Employees
drwxr-xr-x Finance
drwxr-xr-x HR
drwxr-xr-x IA
drwxr-xr-x Management
```

Explanation of permission format:

| Symbol | Meaning       |
| ------ | ------------- |
| `d`    | directory     |
| `r`    | read          |
| `w`    | write         |
| `x`    | execute       |
| `-`    | no permission |

---

# Task 2 – Change Folder Permissions

Give the **owner full access** and allow the **group to read and execute**.

```bash
chmod 750 CompanyA/Employees
chmod 750 CompanyA/Finance
chmod 750 CompanyA/HR
chmod 750 CompanyA/Management
```

Permission meaning:

| Number | Permission             |
| ------ | ---------------------- |
| 7      | read + write + execute |
| 5      | read + execute         |
| 0      | no access              |

---

# Task 3 – Modify File Permissions

Allow users to read files but restrict editing.

Example:

```bash
chmod 640 CompanyA/Finance/Salary.csv
chmod 640 CompanyA/HR/Managers.csv
chmod 640 CompanyA/HR/Assessments.csv
```

Explanation:

| Number | Meaning      |
| ------ | ------------ |
| 6      | read + write |
| 4      | read only    |
| 0      | no access    |

This allows:

* Owner → read/write
* Group → read only
* Others → no access

---

# Task 4 – Update Folder Structure

Create a new shared folder for collaboration.

```bash
mkdir CompanyA/SharedFolders/Projects
```

Verify the structure:

```bash
ls -R CompanyA
```

Expected result:

```
CompanyA/
Employees
Finance
HR
IA
Management
SharedFolders
Projects
```

---

# Task 5 – Verify Permission Changes

Check that the permissions were applied correctly.

```bash
ls -lR CompanyA
```

Example result:

```
drwxr-x--- Employees
drwxr-x--- Finance
drwxr-x--- HR
drwxr-x--- Management
```

---

#  Summary

| Task               | Command |
| ------------------ | ------- |
| View permissions   | `ls -l` |
| Change permissions | `chmod` |
| Create folder      | `mkdir` |
| Verify structure   | `ls -R` |

---

#  Key Commands Learned

```
ls
chmod
mkdir
```

These commands are essential for **Linux system administration and file security**.
