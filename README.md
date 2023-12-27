# Azure Database Migration

In this project, you will architect and implement a cloud-based database system on Microsoft Azure, showcasing your hands-on expertise in cloud engineering.

You'll begin by establishing a production environment database. Subsequently, you'll migrate the database to Azure SQL Database, focusing on crucial aspects like data backup, restoration, and automated scheduling. These efforts will strengthen your data management approach.

A pivotal phase of the project involves simulating a disaster recovery scenario with potential data loss. Furthermore, you will explore the complexities of geo-replication and failover configuration to ensure data availability even under challenging conditions.

To enhance security, Microsoft Entra ID integration will be employed to define access roles, adding an extra layer of control and protection.

## Milestone Steps
# 1. Setting up the production enviroment

Using Azure, an account was created through the AI Core organisation. The virtual machine used was a Windows version, where Remote Desktop was installed, and using the appropriate protocol (3389). SQL Server and SQL Server Management Studio (SSMS) were installed on the VM. These tools are essential for proficient database management within your production environment, mirroring the capabilities of a corporate database server. The AdevntureWorks database was restored locally.

# 2. Migrate to Azure SQL database

A SQL database was created on Azure, to be bale to migrate the on-premises database to the Cloud. The server used an SQL authentication method for a more secure login. Using Azure Data Studio, the Azure Database connection was established. Using SQL Server Schema Compare, this enabled to compare and migrate the scheme from the on premises to the Azure SQL database. The data was then migrated, to transfer the data from the on premise database to the Azure SQL database.

# 3. Data Backup and Restore

A backup production database was created. The database is duplicated to provide a safety net of unforseen issues. To make sure the upload is secure, it was uploaded to the Azure Blob Storage. A new VM was created to develop a 'sandbox' enviroment. Using SSMS Management Task, this automates regular backups of the development database.

# 4. Disaster Recovery Simulation

Critical data was removed from the database to mimic a compromise of data integrity.

`UPDATE TOP (100) Sales.Customer
SET AccountNumber = NULL`

`ELETE TOP (100)
FROM Sales.CreditCard;`

The database was then restored just before the point where the data loss occured. The restored database is now the main production enviorment.

# 5. Geo Replication and Failover

A geo-replication of the production enviroment was set up on Azure. Tjis was set up in the US-East region, to bolster redundancy and resilience. A planned failover was created to check the data consitency of the failover database.

# 6. Microsoft Entra Directory Inegration

Microsoft Entra ID enables a trusted provider to allow only the users authenticated to access the database. The 'db_datareader' role was then provided to the DB reader user to give them read only privleges.