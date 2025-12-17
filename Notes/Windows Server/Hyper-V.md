Hardware virtualization role in Windows Server
Controls access to hardware
Drivers are installed in the host OS

Use Systeminfo.exe to verify the hardware requirements

## Virtual hard disks
Formats:
	- .vhd
	- .vhdx
	- .vhds

Disk Types:
	- Fixed-size (Takes away from physical storage)
	- Dynamically expanding (Only uses what it needs, expanding up to limit)
	- Pass-through
	- Difference (Similar to containers, has parent disk and VMs use that disk but write changes to their own disk)

(The free space shown by dynamically expending virtual hard disks is not equal to physical free space)


## Networks
Adapters:
	- External (out on the internet)
	- Internal (talk to host)
	- Private
You can config VLANS, capture data and filter data travelling through a switch

Have more than one NIC (good practice)
Ensure you have bandwidth management

## Generations
To do with the hardware on machines
Generation 1 is the older hardware
Generation 2 is the standard

Gen 2 have the hot adding feature! Meaning OU can add memory while the machine is running

## Checkpoints
Allow admins to create a snapshot of the current state of a VM
These are not backups they are stored in the same location.

