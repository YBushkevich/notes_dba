

## Type of Oracle Background Processes 
1. Mandatory Background Processes
2. Optional Background Processes
3. Slave Processes

## Mandatory Background Processes
	
The mandatory backgorund processes are present in all typical database configurations. Thes processes run by default in a database instacne started with a minimally configured initialization parameter file.

	1. PMON | Process Monitor — monitors the other background processes and performs process recovery when a server or dispatcher process terminates abnormanlly. 
	2. SMON | System Monitor — perform critial tasks such as crash recovery when the instance is started following a failure, dead transaction recovery, amd maintenance tasks such as temporary space reclamation, data dictionary cleanup, and undo tablespace management.
	3. DBWn | Database Writer — writes modified blocks from the database buffer cache to the data files.
	4. LGWR | Log Writer — writes redo entries to the online redo log.
	5. CKPT | Checkpoint — signals DBWn at checkpoints and updates all the data files and control files of the database to indicate the most recent checkpoint.
	6. MMON | Manageability Monitor — performs many tasks related to manageability, inlcluding taking Automatic Workload Repository snapshots and performing Automatic Database Diagnostic Monitor alalysis.
	7. MMNL | Manageability Monitor Lite — performs tasks relating to manageability, including active session history sampling and metrics computation. 
	8. RECO | Recoverer Process — resolves distributed transactions that are pending because of a network or system failure in a distributed database.


## Optional Background Processes
	
An optional background process is any background process not defined as mandatory. This would include background processes that are specific to tasks or features installed in a database. For example, the ARCn process only exists when the database is in ARCHIVELOG mode and automatic archiving is enabled. Also, there are many background processes only needed to support Oralce Automatic Storage Management (ASM).

	1. ARCn | Archiver — copies the redo log files to archival storage when they are full or an online redo log switch occurs.
	2. CJQ0 | Job Queque Coordinator — selects jobs that need to be run from the data dictionary and spawns job queue slave processes (Jnnn) to run the jobs.
	3. SMCO | Space Management Coordinator — coordinates the execution of various space management tasks.

## Slave Processes

Slave processes are background processes that perform work on behalf of other processes. This section describes some slave processes used by Oracle Dtabase.

	1. Innn | Disk and Tape I/O Slave Process — serves as an I/O slave process spawned on behalf of DBWR, LGWR, or an RMAN backup session.
	2. Pnnn | Parallel Query Slave Process — perform parallel execution of an SQL statement (query, DML, or DDL)
	3. Jnnn | Job Queue Slave Process — executes jobs assigned by the job coordinator.

## V$BGPROCESS view


V$BGPROCESS displays information about the background processes

	1. PADDR 












