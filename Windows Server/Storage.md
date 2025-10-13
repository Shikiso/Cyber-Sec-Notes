### Partition table format
MBR (Master Boot Record):
	- Standard format
	- Supports max 4 primary partitions per drive
	- Can partition a disk up 2TB
GPT:
	- Successor of MBR
	- Supports max or 128 parititons per drive
	- Partititon disk up to 18 exabytes

### Dsik types
Basic disks:
	- Initialized for basic storage
	- Default storage for the windows OS

Dyanmic disks:
	- Modified without restarting
	- Provide serveral options for configuating volumes

Disk volume requirements:
	- System volumn for hardware-specifc files that are required to start the server
	- Boot volume for the Windwos OS files

### File system
FAT (File Allocation Table):
	- Basic file system
	- Partititon size limitations
	- FAT32 to enable larger disks 2TB
	- exFAT developed for flash drives
	- Cannot resize

NTFS:
	- Metadata
	- Auditing and journaling
	- Security (ACLs and encryption)
	- Can extend or shrink

ReFS (Resilient File System):
	- Backward compatibility support for NTFS
	- Enhanced data verification and error correction
	- Suppot for larger files, directories and volumes
	- Can only extend

### Virtual Hard disks
Files that you can use the same way as physical hard disks

You can:
	Create and manage virtal hard disks by using Disk Management and Diskpart.exe
	Configure .vhd or .vhdx files
	Configure computers to start from virtual hard disk
	Transfer virtual hard disks from Hyper-V servers, and start computers from the virtual hard disk
	Use virtual hard disks as a deployment tech

### Disk volumes
Windows Server supports:
	- Simple
	- Spanned
	- Striped
	- Mirrored
	- RAID-5

### RAID
Combines multiple disks into a single logical unit to provide fault tolerance and performance benefits
Provides fault tolerance:
	Uses Disk mirroring and parity information
Provides performance benefits (spreads disk I/O across multiple disks)
Can be configured using several different levels
Should not replace server backups

RAID 0 - Striped set without parity or mirroring
RAID 1 - Mirrored drives
RAID 5 - Block-level striped set with parity distributed across all disks
RAID 6 - ^^^
