# Linux Backup Lab

This project demonstrates how to:
- Create a backup using `tar`
- Log the backup information
- Move the backup file to another folder

---

# Folder Structure
/home/ec2-user/CompanyA/
├── Employees/
│ └── Schedules.csv
├── Finance/
│ └── Salary.csv
├── HR/
│ ├── Assessments.csv
│ └── Managers.csv
├── IA/
├── Management/
│ ├── Promotions.csv
│ └── Sections.csv
└── SharedFolders/


---

# Create a Backup

Check the current directory:

```bash
pwd

# Verify the folder structure:

ls -R CompanyA

# Create the backup:

tar -csvpzf backup.CompanyA.tar.gz CompanyA

# Verify the backup file:

ls

# Log the Backup

cd /home/ec2-user/CompanyA

# Create the log file:

touch SharedFolders/backups.csv

# Write the backup information:

echo "25 Aug 2021, 16:59, backup.CompanyA.tar.gz" | sudo tee SharedFolders/backups.csv

# Check the log file:

cat SharedFolders/backups.csv

# Move the backup file to the IA folder:

mv ../backup.CompanyA.tar.gz IA/

# Verify the file location:

ls . IA


---

# Summary

Task	Command

Create backup	tar -csvpzf backup.CompanyA.tar.gz CompanyA

Log backup	`echo ...

Move backup	mv ../backup.CompanyA.tar.gz IA/
