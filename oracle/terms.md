
1. Instance —

2. Oracle Universal Installer (OUI) — is a graphical user interface utility that enables you to install new Oracle Databse software.
3. Databse Configuration Assistant (DBCA) - 
4. ASM | Automatic Storage Maganement — is a volume manager and a file system for Oracle database files.
5. UGA | User global area — session memory that stores session variables, such as logon information, and can also contain the OLAP pool.
6. OLAP | Online Analytical Processing — OLAP is characterized by dynamic, dimensional analysis of historical data.
7. large pool — optional area in the SGA that provides large memory allocations for backup and restore operations, I/O server processes, and session memory for the shared server and Oracle XA.
8. SGA | System global area — a group of shared memory structures that contain data and control information for one Oracle database instance.
9. control file — a binary file that records the physical structure of a database and contains the names and locations of redo log files, the time stamp of the database creation, the current log sequence number, checkpoint information, and so on.
10. redo log — a set of files that protect altered database data in memory that has not been written to the data files. The redo log can consists of two parts: the online redo log and the archived redo log.
11. archived redo log — groups of redo log files to one or more offline destinations, known collectively as the archived redo log.
12. SCN | System Change Number — a database ordering primitive. The value of an SCN is the logical point in time at which changes are made to a database.
13. AWR | Automatic Workload Repository (AWR) — a buit-in repostiory in every Oracle database. Oracle Datatbase periodically makes a snapshot of its vital statistics and workload information and stores then in AWR.
14. ARCn | Archiver Processes (ARCn) — copy online redo log files to offline storage after a redo log switch occurts. These processes can also collect transaction redo data and transmit it to standby database destinations. ARCn processes exist only when the database is in ARCHIVELOG mode and automatic archiving is enabled.
15. DDL | Data Definition Language — consists of the SQL commands that can be used to define the database schema. It simply deals with descriptions of the database schmea and is used to create and modify the structure of database objects in the database. (CREATE, RENAME)
16. DML | Data Manipulation Language — command that deals with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements. (INSERT, UPDATE, DELETE) 
17. [What is data dictionary?](https://www.quora.com/What-is-a-data-dictionary-in-Oracle) data dictionary — a read-only collection of databse tables and views containing reference information about the database, its structures, and its users.
18. [What is view?](https://stackoverflow.com/questions/256700/what-is-a-view-in-oracle) view — representation of a SQL statement that is stored in memory so that it can easily be re-used.  
19. operating system block — the smallest unit of operating system I/O.
20. block overhead — space in a data block that stores metadata required for managing the block. The overhead includes the block header, table directory, and row directory.
21. table compression — the compression of data segments to reduce disk space in a heap-organized table or table partition.
22. heap-organized table — a table in which the data rows are stored in no particular order on disk. By default, `CREATE TABLE` creates a heap-organized table.	
23. RAID | redundant array of independent disks — is a way of storing the same data in different places on multiple hard disks to protect data in the case of a drive failure.
24. LOB | large object — an Oracle data type designed to hold large amount of data.












 
