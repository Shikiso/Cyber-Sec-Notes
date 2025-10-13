Bottleneck is a resource that is currently at peak utilization

## Manging AD DS
The directory databse stores AD information
Four AD partitions on each domain contoller are: domain, configuration, schema and application
File-level components of the AD DS database are:
Ntds.dit	- Main AD DS database file, contains AD partitions and objects
Edb*.log	- Transaction logs
Edb.chk		- Database checkpoint file
Edbres00001.jrs - Reserver transaction log file that allows the dir to process tranactions
Edbres00002.jrs

### NtdsUtil
Manage and control single-master operations
Perform AD DB maintenance:
	- Perform offline defragmentation
	- Create and mount snapshots
	- Move database files
Clean domain-controller metadata:
	- Domain-controller removal or demotion while not connected to a domain
Reset DSRM:
	- Password
	- set dsrm
