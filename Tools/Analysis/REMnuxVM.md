REMnix VM is a specialized Linux distro, providing a sandbox-like environment for dissecting potentially malicious software without risking your primary system.
# oledump.py
`oledump.py` is a python tool that analyzes OLE2 files.
Usage: `oledump.py [filename`]

When reading the results if you see a `M` in one of the streams that means there is a macro and you might want to check out this stream.
To check out the stream run the command: `oledump.py [filename] -s [stream_num]`
(`-s` is short for `-select`)

**Example Output:**
```
ubuntu@MACHINE_IP:~/Desktop/tasks/agenttesla$ oledump.py agenttesla.xlsm 
A: xl/vbaProject.bin
 A1:       468 'PROJECT'
 A2:        62 'PROJECTwm'
 A3: m     169 'VBA/Sheet1'
 A4: M     688 'VBA/ThisWorkbook'
 A5:         7 'VBA/_VBA_PROJECT'
 A6:       209 'VBA/dir'
```

Using the additional parameter `--vbadecompress` will automatically decompress and compressed VBA macros.
# INetSim
INetSim is a tool inside of REMnux VM which can start a fake network keeping the real network secure.
To do this first we need to change the IP address.
1. Open /etc/inetsim/inetsim.conf
2. Edit `dns_default_ip` and set it to your IP
3. Run `sudo inetsim`
4. Let it run and have the malware do its thing
5. Stop INetSim and read the generated report

# Volatility
Used to identify and extract specific artifacts from memory images.
To use the plugins run `vol3 -f wcry.mem` followed by the plugin.
### PsTree
This plugin lists processes in a tree based on their parent process ID.
```powershell
root@MACHINE_IP:/home/ubuntu/Desktop/tasks/Wcry_memory_image$ vol3 -f wcry.mem windows.pstree.PsTree
Volatility 3 Framework 2.0.0
Progress:  100.00		PDB scanning finished
```
### PsList
This plugin is used to list all currently active processes in the machine.

```powershell
root@MACHINE_IP:/home/ubuntu/Desktop/tasks/Wcry_memory_image$ vol3 -f wcry.mem windows.pslist.PsList
Volatility 3 Framework 2.0.0
Progress:  100.00		PDB scanning finished
```
### CmdLine
This plugin is used to list process command line arguments.

```powershell
root@MACHINE_IP:/home/ubuntu/Desktop/tasks/Wcry_memory_image$ vol3 -f wcry.mem windows.cmdline.CmdLine
Volatility 3 Framework 2.0.0
Progress:  100.00		PDB scanning finished
```
### FileScan
This plugin scans for file objects in a particular Windows memory image. The results have more than 1,400 lines.

```powershell
root@MACHINE_IP:/home/ubuntu/Desktop/tasks/Wcry_memory_image$ vol3 -f wcry.mem windows.filescan.FileScan
Volatility 3 Framework 2.0.0
Progress:  100.00		PDB scanning finished
```
### DllList
This plugin lists the loaded modules in a particular Windows memory image. Due to a text limitation, this one won't have a View Results icon.

```powershell
root@MACHINE_IP:/home/ubuntu/Desktop/tasks/Wcry_memory_image$ vol3 -f wcry.mem windows.dlllist.DllList
Volatility 3 Framework 2.0.0
Progress:  100.00		PDB scanning finished
```
### PsScan
This plugin is used to scan for processes present in a particular Windows memory image.

```powershell
root@MACHINE_IP:/home/ubuntu/Desktop/tasks/Wcry_memory_image$ vol3 -f wcry.mem windows.psscan.PsScan
Volatility 3 Framework 2.0.0
Progress:  100.00		PDB scanning finished
```
### Malfind
This plugin is used to lists process memory ranges that potentially contain injected code. There won't be any View Results icon for this one due to text limitation.
```powershell
root@MACHINE_IP:/home/ubuntu/Desktop/tasks/Wcry_memory_image$ vol3 -f wcry.mem windows.malfind.Malfind
Volatility 3 Framework 2.0.0
Progress:  100.00		PDB scanning finished
```
