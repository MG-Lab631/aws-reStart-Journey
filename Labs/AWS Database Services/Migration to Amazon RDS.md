# ☕ CafeDB Migration to Amazon RDS 

##  Overview

Database Migration 

Database migration is the process of moving data, schema, and database functionality from one system to another while preserving integrity, availability, and performance.

---

##  This project shows how to:

* Transition from an instance-based database to a managed service
* Configure secure networking between compute and database layers
* Provision database infrastructure programmatically
* Perform a database migration using native tools
* Validate connectivity and monitor database activity

---

## Architecture Evolution

### Before Migration

* Database hosted directly on a compute instance (MariaDB)
* Tight coupling between application and database
* Manual configuration and maintenance

### After Migration

* Database hosted on Amazon RDS (managed service)
* Application connects via RDS endpoint over private network
* Infrastructure managed through AWS services and automation

##  Architecture Diagram

<img width="889" height="1010" alt="179 cafedb_architecture" src="https://github.com/user-attachments/assets/103a5f95-dcfb-49de-b9be-a8d5310b711e" />

---

## ⚙️ Infrastructure & Configuration

### 🔐 Network Access Control

To allow communication between the application instance and the database, security group rules were configured to permit MySQL traffic (port 3306) between resources.

This ensures:

* Controlled, internal-only access
* No public exposure of the database

---

### 🌐 Private Subnet Design

Two private subnets were created across different availability zones:

* Enables high availability
* Ensures the database is isolated from public internet access
* Forms the foundation for the database subnet group

---

### 🗄️ RDS Subnet Group

A dedicated DB subnet group was defined using the private subnets.

This allows the RDS instance to:

* Operate within isolated network boundaries
* Support multi-AZ deployments if needed
* Integrate cleanly into the VPC architecture

---

### 🛠️ RDS Instance Provisioning

The MariaDB RDS instance was created with:

* Engine: MariaDB (10.11.x)
* Instance type: db.t3.micro
* Private accessibility (no public endpoint)
* Attached VPC security group
* Defined subnet group

Provisioning was done via AWS CLI, demonstrating infrastructure-as-code principles.

---

## 🔄 Data Migration Approach

Instead of using specialized migration tools, a **native dump-and-restore strategy** was used:

### 📤 Export

* Database content was exported into a `.sql` backup file

### 📥 Import

* The backup was restored into the RDS instance using a secure MySQL connection

This approach is:

* Simple and reliable
* Ideal for small-to-medium datasets

<img width="998" height="868" alt="Lab 179 - AWS Cafe order History with RDS" src="https://github.com/user-attachments/assets/1d14afdd-5a60-4065-8ec9-db586b099346" />


---

## 🔗 Secure Connectivity

Connections to the RDS instance were established using:

* RDS endpoint (DNS-based)
* SSL certificate (`global-bundle.pem`)
* Standard MySQL client

This ensures:

* Encrypted communication
* Authentication via database credentials
* Secure data transfer during migration

<img width="889" height="730" alt="Lab 179 Mariadb select from product" src="https://github.com/user-attachments/assets/0a21cd83-06ef-419d-b853-0f726fd33d38" />

---

## 📊 Validation & Monitoring

After migration, validation included:

* Querying tables (e.g., `product`)
* Verifying row counts and data integrity
* Confirming successful connections from the application host

Additionally, monitoring metrics such as:

* Database connections
* Instance status

were observed to ensure the system was functioning as expected.

<img width="653" height="820" alt="Lab 179 - CafedbConnections with Cloud Watch" src="https://github.com/user-attachments/assets/cd23e91c-a81a-4976-bcea-5701b043f78a" />

<img width="753" height="855" alt="Lab 179- DB Log, events" src="https://github.com/user-attachments/assets/06b77c1a-bca8-411e-8c71-1e1be9cd26de" />

---

##  Key Outcomes

* Successfully migrated a live database to a managed service
* Implemented secure, private connectivity within a VPC
* Practiced AWS CLI for infrastructure provisioning
* Validated end-to-end database functionality post-migration

---

## Lessons Learned

* Network configuration is critical for RDS accessibility
* Cloud monitoring tools may have slight delays
* Managed services reduce operational burden but require proper setup
* Even simple migrations involve multiple layers (network, compute, database)

---

##  Final Thoughts

This project highlights the transition from manual infrastructure management to cloud-native, managed services.

It demonstrates not just *how* to migrate a database, but how different AWS components work together to support a scalable and secure architecture.

---

