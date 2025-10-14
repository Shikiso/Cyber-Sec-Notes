Show usable WLAN interfaces
`airmon-ng`

Show processes that can interfere with aircrack-ng
`airmon-ng check (Add kill to kill these processes)`

Start or Stop interface (MANDATORY)
`airmon-ng <start|stop> <interface>`

Set the NIC to specific channel
`airodump-ng --channel <channel> (can use -c instead of --channel)`

Capture data
`airodump-ng <interface>`
`--channel <channel> (for specific channel)`
`--bssid <bssid> (for specific network)`
`-w <directory> (write output to file)`

Crack handshake
`aircrack-ng -a2 -w <dictionary> <cpature.cap>`
`a2 (-a force attack mode) (1 WEP | 2 WPA-PSK)`