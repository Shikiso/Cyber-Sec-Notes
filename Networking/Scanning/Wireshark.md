Wireshark is used to capture network traffic which can then be analysed.

# Filters
There are two types of filters:
1. Capture filter - this filters out in the capture process, so that it does not capture what you have no specified.
2. Display filter - This filters what you see. You could have captured 1000 packets but using the display filter you will only be shown 100 that are relevant.

# Syntax
## Capture Filter
Click on the fourth icon from the left. (Will say `Capture Options` when you hover)
A useful filter might be from a specific host with a specific port
```
host 192.168.1.102
port 110
```

## Display Filter
Same filter but now it looks like. This is in the text box
```
ip.addr == 192.168.1.102
tcp.port eq 25
```
