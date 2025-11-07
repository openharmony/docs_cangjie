# Overview of Data Reliability and Security  

## Functional Scenarios  

During system operation, storage corruption, insufficient storage space, file system permissions, and power failures may cause database malfunctions. For example, corruption of a contacts application's database could result in loss of user contacts; corruption of a calendar application's database could lead to missed calendar reminders. To address these issues, data management provides solutions and capabilities to ensure data reliability and security.  

- **Backup and Recovery**: In critical business applications (e.g., banking), severe data loss scenarios can be mitigated by restoring databases from backups, ensuring key data is preserved.  
- **Database Encryption**: When storing highly sensitive information such as authentication credentials or financial data, databases can be encrypted to enhance security.  
- **Data Classification and Grading**: During cross-device data synchronization, data management enforces access control based on data security labels and device security levels to safeguard data.  
- **Class E Encrypted Databases**: Applications storing sensitive user information should use Class E databases. Under certain conditions (e.g., device lock screen), the encryption key is destroyed, rendering Class E databases inaccessible. Upon unlocking, the key is restored, and normal read/write operations resume, ensuring sensitive data security.  

Additionally, backup databases are stored within the application's sandbox. When storage space is insufficient, local database backups can be deleted to free up space.  

## Basic Concepts  

Before developing features related to data reliability and security, familiarize yourself with the following concepts.  

### Database Backup and Recovery  

- **Database Backup**: Refers to creating a complete backup of the current database file. OpenHarmony database backup performs a full backup of all database files. The database does not need to be closed during backup; simply call the backup interface to complete the process.  
- **Database Recovery**: Restores the current database file from a specified backup file. Upon completion, the current database data matches the state of the specified backup file.  

### Database Encryption  

Database encryption involves encrypting the entire database file, enhancing security and effectively protecting database contents.  

### Data Classification and Grading  

Distributed data management implements classification and grading protection for data, providing access control mechanisms based on data security labels and device security levels.  

Higher data security labels and device security levels correspond to stricter encryption and access control measures, ensuring greater data security.  

## Operational Mechanisms  

### Database Backup and Recovery Mechanism  

During backup, the current database is saved to a specified file. Subsequent database operations do not affect the backup file. Only when recovering from a specified backup file will the current database be overwritten, enabling data rollback.  

- **Key-Value Database Backup Path**: `/data/service/el1(el2)/public/database/...{appId}/kvdb/backup/...{storeId}`  
- **Relational Database Backup Path**: `/data/app/el1(el2)/100/database/...{bundlename}/rdb`  

### Database Encryption Mechanism  

In OpenHarmony, database encryption does not require developers to provide encryption keys. Instead, developers only need to set the database encryption state. The system automatically handles encryption using the [HUKS Universal Keystore System](../reference/UniversalKeystoreKit/cj-apis-security_huks.md), generating and protecting database encryption keys.  

## Constraints  

- Database encryption keys are automatically rotated once per year.  
- A maximum of 5 backups are allowed for key-value databases.  
- Automatic backups for key-value databases require the device to be in a locked screen and charging state.