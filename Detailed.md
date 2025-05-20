# IP Address Details

# IPv4 and IPv6

IP was designed as a Layer 3 connectionless protocol. It provides the necessary functions to deliver a packet from a source host to a destination host over an interconnected system of networks. The protocol was not designed to track and manage the flow of packets. These functions, if required, are performed primarily by TCP at Layer 4.

IP makes no effort to validate whether the source IP address contained in a packet actually came from that source. For this reason, threat actors can send packets using a spoofed source IP address. In addition, threat actors can tamper with other fields in the IP header to carry out their attacks. Therefore, it is important for security analysis to understand the different fields in both the IPv4 and IPv6 headers.

# The IPv4 Packet Header

The fields in the IPv4 packet header are shown in the figure.

## IPv4 Packet Header

### Version

- Contains a 4-bit binary value set to 0100 that identifies this as an IPv4 packet.

### Internet Header length

- A 4-bit field containing the length of the IP header.
- The minimum length of an IP Header is 20 bytes.

### Differentiated Services or DiffServ (DS)

- Formerly called the Type of Service (ToS) field, the DS field is an 8-bit field used to determine the priority of each packet.
- The six most significant bits of the DiffServ field are the Differentiated Services Code Point (DSCP).
- The last two bits are the Explicit Congestion Notification (ECN) bits.

### Total length

- Specifies the length of the IP packet including the IP header and the user data.
- The total length field is 2 bytes, so the maximum size of an IP packet is 65,535 bytes; however, packets are much smaller in practice.

### Identification, Flag and Fragment offset

- As an IP packet moves through the internet, it might need to cross a route that cannot handle the size of the packet.
- The packet will be divided, os fragmented, into smaller packets and reassembled later.
- These fields are used to fragment and reassemble packets.

### Time-to-Live (TLL)

- Contains an 8-bit binary value that is used to limit the lifetime of packet.
- The packet sender sets the inital TLL value, and it is decreased by one each time the packet is processed by a router.
- If the TTL field decrements to zero, the router discards the packet and sends an Internet Control Message Protocol (ICMP) Time Exceeded message to the source IP address.

### Protocol

- Field is used to identify the next level protocol.
- This 8-bit binary value indicates the data payload type that the packet is carrying, which enables the network layer to pass the data to the appropriate upper-layer protocol.
- Common values include ICMP (1), TCP (6), and UDP (17).

### Header checksum

- A value that is calculated based on the contents of the IP header.
- Used to determine if any errors have been introduced during transmission.

### Source IPv4 Address

- Contains a 32-bit binary value that represents the source IPv4 address of the packet.
- The source IPv4 address is always a unicast address.

### Destination IPv4 Address

- Contains a 32-bit binary value that represents the destination IPv4 adress of the packet.

### Options and Padding

- This is a field that varies in lenght from 0 to a multiple of 32 bits.
- If the option value are not a multiple of 32 bits, 0s are added, padded, to ensure that this fields contains a multiple of 32 bits.
