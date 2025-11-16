All operating systems are comprised of two components, the kernel and the user land.

The kernel is situated at the center of your OS, it has the power of controlling each and every functioning of the OS. This includes the function of CPU control, memory management and control over the content a user can see on the screen.

The kernel of an OS has been designed in a way to perform as a privileged or protected area which is possible to access by any other form of account which is privileged as well.

# What is Kernel Module?
To put it simple think of the kernel as the central nervous system of the OS.
It controls every function of the OS and includes the management of interaction in between the components of hardware and the starting of required services.

Linux is an imposing type of kernel allowing the adding up of the kernel modules. In general the modules can be removed/added from the kernel according to the users needs.

Some OS which need the kernel to be completely rebuilt, assembled and rebooted when adding a driver for a update. However in Linux it comes with the capability of adding up kernel modules to the system kernel without performing this whole process. These modules are known as LKMs or Loadable Kernel Modules.

LKMs are powered with the access of kernel to the lowest levels. This makes them a very easy target for all the attackers.

# Management of Kernel Modules
Linux comes with two varied ways in which kernel modules can be managed.
1. Using a command group which is built in the suite of `insmod` (which stands for insert module). 
2. Using the command `modprobe` This command is used for management of LKMs. For adding a kernel module using `modprobe` you need to use the command with `-a` switch. For removing use the `-r`.