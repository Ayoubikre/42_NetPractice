*This project has been created as part of the 42 curriculum by aakritah.*

# 🌐 NetPractice

A practical introduction to computer networking through hands-on IP configuration exercises. NetPractice teaches the fundamentals of TCP/IP addressing, subnetting, and network topology through 10 progressively challenging levels.

## 📋 Description

NetPractice is an interactive training platform designed to build foundational networking knowledge. Through a browser-based interface, you'll configure small-scale networks by setting IP addresses, subnet masks, and routing tables to make non-functioning networks operational.

The project covers essential networking concepts including IP addressing schemes, subnet calculations, gateway configuration, and understanding how devices communicate within and between networks. Each of the 10 levels presents a unique networking scenario that must be solved by correctly configuring the available network parameters.

**Learning Objectives:**
- Understand TCP/IP addressing and how it enables network communication
- Master subnet masks and network segmentation
- Configure routing between networks using gateways
- Distinguish between private and public IP ranges
- Learn the practical application of networking theory

## 🚀 Instructions

### Running the Training Interface

1. **Download and extract** the project files from the intranet
2. **Navigate** to the extracted folder in your terminal
3. **Launch the interface** by running:
   ```bash
   ./run.sh
   ```
   This will start a local web server and open the training interface in your browser.

**Alternative method** (if run.sh doesn't work):
```bash
python3 -m http.server 49242
```
Then navigate to `http://localhost:49242` in your web browser.

### Using the Interface

**Training Mode:**
- Enter your 42 login in the designated field
- This loads your personal configuration and progress
- Complete all 10 levels in sequence

**Evaluation Mode:**
- Use the "evaluation" tab for random configurations
- Useful for practice and peer evaluations

### Completing Levels

For each level:
1. **Analyze** the network diagram and identify what's broken
2. **Check objectives** at the top of the screen
3. **Configure** the unshaded fields (IP addresses, subnet masks, routes)
4. **Validate** your solution using the `Check again` button
5. **Export** your configuration with the `Get my config` button
6. **Save** the exported file before moving to the next level

### Exporting Configurations

**IMPORTANT:** After completing each level, you must export your configuration:
- Click the `Get my config` button
- Save the downloaded file (e.g., `level1.json`, `level2.json`, etc.)
- These files are required for submission

### Submission Requirements

Your Git repository must contain:
- **10 configuration files** (one per level) at the repository root
- **README.md** (this file)
- Files should be named clearly (e.g., `level1.json` through `level10.json`)

```
your-repository/
├── README.md
├── level1.json
├── level2.json
├── level3.json
├── level4.json
├── level5.json
├── level6.json
├── level7.json
├── level8.json
├── level9.json
└── level10.json
```

**During Defense:**
You will complete 3 random levels in a limited time without external tools (only basic calculator like `bc` is allowed).

## 🧠 Networking Concepts Covered

### TCP/IP Addressing
**IP addresses** uniquely identify devices on a network. In IPv4, they consist of 4 octets (32 bits total), written in decimal notation like `192.168.1.1`.

**IP Address Classes:**
- **Class A**: `1.0.0.0` to `126.255.255.255` (for very large networks)
- **Class B**: `128.0.0.0` to `191.255.255.255` (for medium-sized networks)
- **Class C**: `192.0.0.0` to `223.255.255.255` (for small networks)

**Private IP Ranges** (not routable on the internet):
- `10.0.0.0` to `10.255.255.255` (Class A)
- `172.16.0.0` to `172.31.255.255` (Class B)
- `192.168.0.0` to `192.168.255.255` (Class C)
- `127.0.0.0` to `127.255.255.255` (Loopback)

### Subnet Masks
A **subnet mask** determines which portion of an IP address represents the network and which represents the host.

**Common subnet masks:**
- `/24` or `255.255.255.0` - 256 addresses (254 usable hosts)
- `/25` or `255.255.255.128` - 128 addresses (126 usable hosts)
- `/26` or `255.255.255.192` - 64 addresses (62 usable hosts)
- `/27` or `255.255.255.224` - 32 addresses (30 usable hosts)
- `/28` or `255.255.255.240` - 16 addresses (14 usable hosts)
- `/30` or `255.255.255.252` - 4 addresses (2 usable hosts, for point-to-point links)

**CIDR Notation:**
Instead of writing `255.255.255.0`, we use `/24` to indicate 24 network bits.

**Calculating network ranges:**
```
IP:          192.168.1.50
Subnet:      255.255.255.0 (/24)
Network:     192.168.1.0
Broadcast:   192.168.1.255
Usable IPs:  192.168.1.1 - 192.168.1.254
```

### Default Gateway
The **gateway** (or default gateway) is the router's IP address that connects your local network to other networks. Devices send traffic destined for other networks to this gateway.

**Gateway requirements:**
- Must be on the same subnet as the host
- Must be a valid IP within the network range
- Typically the router's interface IP on that network

**Example:**
```
Host IP:     192.168.1.10/24
Gateway:     192.168.1.1
Network:     192.168.1.0/24

This host can communicate with 192.168.1.x directly,
but needs the gateway (192.168.1.1) to reach 10.0.0.x
```

### Routers
**Routers** connect different networks and forward packets between them. They have multiple interfaces, each with an IP address on a different network.

**Routing tables** tell routers where to send packets:
- **Destination**: Target network
- **Next hop**: Where to send packets for that destination
- **Default route** (`0.0.0.0/0`): Where to send packets when no specific route matches

### Switches
**Switches** connect devices within the same network. Unlike routers:
- They operate at Layer 2 (Data Link Layer)
- They don't route between different networks
- They forward frames based on MAC addresses

In NetPractice, switches are mostly transparent - devices connected to the same switch are on the same network segment.

### OSI Model Layers (relevant to this project)

**Layer 3 - Network Layer:**
- Handles IP addressing and routing
- Routers operate here
- Determines the path packets take across networks

**Layer 2 - Data Link Layer:**
- Handles MAC addressing and frame switching
- Switches operate here
- Manages direct node-to-node transfer

**Layer 1 - Physical Layer:**
- Physical cables and connections
- Actual transmission of raw bits

## 💡 Key Concepts & Tips

### Understanding Subnetting

**Why subnet?**
- Divide large networks into smaller, manageable segments
- Improve security and performance
- Reduce broadcast traffic

**Subnet calculation formula:**
```
Number of hosts = 2^(32 - prefix_length) - 2

Examples:
/24 = 2^(32-24) - 2 = 2^8 - 2 = 254 hosts
/25 = 2^(32-25) - 2 = 2^7 - 2 = 126 hosts
/30 = 2^(32-30) - 2 = 2^2 - 2 = 2 hosts
```

We subtract 2 because:
- Network address (all host bits = 0) is reserved
- Broadcast address (all host bits = 1) is reserved

### Common Mistakes to Avoid

❌ **IP and gateway on different subnets**
```
IP:      192.168.1.10/24
Gateway: 192.168.2.1      ← Wrong! Different network
```

✅ **Correct configuration**
```
IP:      192.168.1.10/24
Gateway: 192.168.1.1      ← Same network
```

❌ **Using network or broadcast address**
```
Network:     192.168.1.0/24
IP assigned: 192.168.1.0   ← Network address, invalid!
IP assigned: 192.168.1.255 ← Broadcast address, invalid!
```

✅ **Using valid host addresses**
```
Network:     192.168.1.0/24
IP assigned: 192.168.1.1 to 192.168.1.254
```

❌ **Overlapping subnets**
```
Interface A: 192.168.1.0/24
Interface B: 192.168.1.128/25 ← Overlaps with Interface A!
```

### Problem-Solving Strategy

1. **Identify the network topology**: How many networks? How are they connected?
2. **Check the objectives**: What needs to communicate with what?
3. **Plan your subnets**: Ensure no overlaps, appropriate sizes
4. **Configure IPs**: Keep devices on the same network together
5. **Set gateways**: Point to the router interface on the local network
6. **Configure routing**: Ensure routers know how to reach all networks
7. **Validate**: Use the checker and read error messages carefully

## 🔧 Practical Examples

### Example 1: Simple Network
```
[ PC A ] --- [ Switch ] --- [ PC B ]

Requirements:
- PC A and PC B must communicate
- Both on the same network

Solution:
PC A:  192.168.1.10/24
PC B:  192.168.1.20/24
(No gateway needed - same network, direct communication)
```

### Example 2: Two Networks with Router
```
[ PC A ] --- [ Router ] --- [ PC B ]
             Interface1   Interface2

Requirements:
- PC A (left) must reach PC B (right)

Solution:
PC A:        10.0.0.10/24,    Gateway: 10.0.0.1
Router Int1: 10.0.0.1/24
Router Int2: 192.168.1.1/24
PC B:        192.168.1.10/24, Gateway: 192.168.1.1
```

### Example 3: Subnet Division
```
Network: 192.168.1.0/24
Need to create 4 subnets

Solution (/26 gives 4 subnets of 64 IPs each):
Subnet 1: 192.168.1.0/26   (192.168.1.1   - 192.168.1.62)
Subnet 2: 192.168.1.64/26  (192.168.1.65  - 192.168.1.126)
Subnet 3: 192.168.1.128/26 (192.168.1.129 - 192.168.1.190)
Subnet 4: 192.168.1.192/26 (192.168.1.193 - 192.168.1.254)
```

## 📚 Resources

### Essential Reading
- [**TCP/IP Guide**](http://www.tcpipguide.com/) - Comprehensive networking resource
- [**Subnet Calculator**](https://www.subnet-calculator.com/) - For practice and verification
- [**RFC 791 - Internet Protocol**](https://tools.ietf.org/html/rfc791) - Official IP specification
- [**RFC 1918 - Private Address Allocation**](https://tools.ietf.org/html/rfc1918) - Private IP ranges

### Tutorials & Guides
- [**Subnetting Made Easy**](https://www.youtube.com/watch?v=BWZ-MHIhqjM) - Video tutorial on subnetting
- [**IP Addressing and Subnetting for New Users**](https://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13788-3.html) - Cisco guide
- [**Understanding TCP/IP**](https://www.ibm.com/docs/en/aix/7.2?topic=protocol-tcpip-addressing) - IBM documentation

### Networking Fundamentals
- **OSI Model**: Understanding the 7 layers of networking
- **Binary/Decimal Conversion**: Essential for subnet calculations
- **CIDR Notation**: Modern method of IP addressing
- **Routing Protocols**: How routers share information (beyond this project's scope)

### Tools for Practice
- **Subnet calculators**: For verifying your calculations
- **Binary converters**: Understanding IP addresses in binary
- **Network simulators**: Packet Tracer, GNS3 (for deeper learning)

## 🎯 Learning Outcomes

After completing NetPractice, you will be able to:
- ✅ Calculate subnet masks and determine usable IP ranges
- ✅ Configure IP addresses for devices on the same and different networks
- ✅ Set up routing between networks using gateways
- ✅ Identify and fix common networking misconfigurations
- ✅ Understand how packets flow through a network topology
- ✅ Apply binary math to networking problems
- ✅ Read and interpret network diagrams
- ✅ Troubleshoot connectivity issues systematically

---

*Networking might seem abstract at first, but NetPractice makes it tangible. Each level solved deepens your understanding of how the internet actually works. Take your time, understand the concepts, and the solutions will follow naturally.*

*Good luck! 🚀*
