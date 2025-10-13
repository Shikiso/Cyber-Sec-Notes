Get available disks:
Get-Disk | Where-Object PartitionStyle –Eq "RAW"

Initialize disk:
Initialize-disk {number}

Review partition table:
Get-disk

Create a ReFS volume with all available space:
New-Partition -DiskNumber {num} -UseMaximumSize -AssignDriveLetter | Format-Volume -NewFileSystemLabel "NAME" -FileSystem ReFS

Dismount Virtual hard disk:
Dismount-vhd {disk}

Check properties of vhd:
Get-vhd {disk}

Convert VHD to VHDX:
Convert-VHD -Path {disk} -DestinationPath {disk.vhdx}

Change sector size:
Set-VHD –Path {disk} –PhysicalSectorSizeBytes {size}

Optimize .vhdx file:
Optimize-VHD –Path {disk} –Mode Full

## DISKPART
Create new disk using Diskpart:
Diskpart
List disk
Select disk {num}
Convert dynamic
Create volume NAME size={size} disk={num}
Assign letter={letter}
Format

To Extend size:
Extend size {size}

To Shrink size:
Shrink desired={size{