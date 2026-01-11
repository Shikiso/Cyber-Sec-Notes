Subnetting is the process of taking a network and splitting it in to smaller networks called subnets.

A IPv4 address i a 32 bit number. To simplify addresses they are divided into 4 8 bit numbers or octets separated by a decimal point. The octets range from 0 - 255.

The octects can only go up to 255 because the IPv4 address is in binary.
Binary Chart: `128 64 32 16 8 4 2 1`
`192.168.0.1 -> 01100000.01010100.00000000.00000001`
`255.255.255.0 -> 11111111.11111111.11111111.00000000`

A subnet mask is used to determine the host and network portion of an address.
A network portion is what determines what network the host is on.
A host portion defines what host has what address.
In the example 192.168.0.23 with the subnet mask 255.255.255.0. 192.168.0 is the network portion and 23 is the host portion.

To make things easier when knowing where the network portion ends and host portion starts we will convert the previous examples subnet mask into binary.
`11111111.11111111.11111111.00000000`
the `1` decide the network portion and `0` the host portion, meaning there are `253` host addresses since the first and last address are the network and broadcast address.

When writing network addresses you will often see /24 ,/16, /8, etc. These are just the sum of the network portion. So if we convert `255.255.255.0` in to binary there are `24` `1` making it a /24 network.
 
Examples:
`192.168.0.0/16 `
`192.168.0.0 -> 01100000.01010100.00000000.0000000`
`/16 - > 1111111.11111111.00000000.00000000`
Addresses: `192.168.0.0 -> 192.168.255.255`

`172.16.0.0/12`
`172.16.0.0 -> 10101100.00010000.00000000.00000000`
`/12 - > 11111111.11110000.00000000.00000000`
Addresses: `172.16.0.0 -> 172.31.255.255`
(This ones a bit weird but as you can see only 12 binary numbers are allowed for a network address. Leaving 20 binary numbers for host addresses. Meaning 16-31 changes the host address).