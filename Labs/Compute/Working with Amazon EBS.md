# Working with Amazon EBS – Lab Summary

## Lab Overview
Amazon Elastic Block Store (Amazon EBS) provides scalable, high-performance block storage for Amazon EC2 instances. In this lab, you will:

- Create and attach an EBS volume to an EC2 instance
- Create a filesystem and mount the volume
- Take snapshots and restore volumes from snapshots
- 
<img width="606" height="186" alt="W AWS EBS" src="https://github.com/user-attachments/assets/9252bb59-06c5-4c6a-8c9c-37083ec89b5a" />
---

## Objectives
By the end of this lab, you should be able to:

1. Create an EBS volume  
2. Attach and mount the volume to an EC2 instance  
3. Create a snapshot of the volume  
4. Restore a volume from a snapshot  

---

## Task 1: Create a New EBS Volume

1. Open **EC2 Management Console**  
2. Note the Availability Zone of the EC2 instance (e.g., `us-west-2a`)  
3. Navigate to **Elastic Block Store → Volumes → Create volume**

**Volume configuration:**
Volume type: General Purpose SSD (gp2)
Size: 1 GiB
Availability Zone: Same as EC2 instance
Tag: Name = My Volume


4. Click **Create volume** → Status changes from `Creating` → `Available`

---

## Task 2: Attach the Volume to an EC2 Instance

1. Select **My Volume → Actions → Attach volume**  
2. Choose your EC2 instance  
3. Set **Device name** to `/dev/sdb`  
4. Click **Attach volume** → Volume state becomes `In-use`

---

## Task 3: Connect to the EC2 Instance

Use **EC2 Instance Connect** or SSH to access your terminal for the remaining tasks.

---

## Task 4: Create and Configure the File System

```bash
# Verify available storage
df -h

# Create ext3 filesystem on new volume
sudo mkfs -t ext3 /dev/sdb

# Create mount point
sudo mkdir /mnt/data-store

# Mount the volume
sudo mount /dev/sdb /mnt/data-store

# Ensure automatic mounting after reboot
echo "/dev/sdb /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab

# Verify mount
df -h

# Create a test file
sudo sh -c "echo 'some text has been written' > /mnt/data-store/file.txt"

# Verify file content
cat /mnt/data-store/file.txt


Task 5: Create an Amazon EBS Snapshot

Navigate to Volumes → My Volume → Actions → Create snapshot

Add a tag: Name = My Snapshot

Snapshot status: Pending → Completed

# Optional: delete test file after snapshot
sudo rm /mnt/data-store/file.txt
ls /mnt/data-store/file.txt  # Should display: No such file or directory

Task 6: Restore Volume from Snapshot
6.1 Create Volume from Snapshot

Navigate to Snapshots → My Snapshot → Actions → Create volume

Availability Zone: same as original

Tag: Name = Restored Volume → Click Create volume

6.2 Attach Restored Volume

Attach to EC2 instance

Device name: /dev/sdc

Volume state: In-use

6.3 Mount Restored Volume

# Create mount point
sudo mkdir /mnt/data-store2

# Mount the restored volume
sudo mount /dev/sdc /mnt/data-store2

# Verify restored file exists
ls /mnt/data-store2/file.txt

Conclusion: 

Created an EBS volume

Attached and mounted it to an EC2 instance

Created a snapshot of the volume

Restored a volume from a snapshot

