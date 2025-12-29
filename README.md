# NetPractice

*This project has been created as part of the 42 curriculum by Amsbai*

## Description

NetPractice is a practical networking training project designed to teach fundamental concepts of IP addressing, subnetting, and routing. Through 10 progressive levels of increasing difficulty, participants configure network topologies by assigning IP addresses, subnet masks, and routing tables to establish proper communication between hosts and routers.

The goal is to develop a solid understanding of how networks operate at the IP layer, including subnet calculations, network segmentation, and packet routing. Each level presents a network diagram where certain configuration fields are left blank, and the objective is to fill them correctly so that all devices can communicate according to the network requirements.

## Instructions

### Running the Training Interface

1. Download and install NetPractice:
   ```bash
   curl -O https://cdn.intra.42.fr/document/document/43640/net_practice.1.8.tgz
   tar -xzf net_practice.1.8.tgz
   cd net_practice
   ```

2. Open the training interface:
   ```bash
   open index.html
   ```
   Or simply double-click the `index.html` file in your file browser.

3. The interface will load in your web browser, presenting you with an 
	interface where you chose either Training or Evalution.
		Training : You can practice if you input your login in the field, using your personal configuration.
		Evaluation : random configuration, suitable for evaluations.

### Using the Interface

- **Fill in the fields**: Click on empty fields to enter IP addresses, subnet masks, or routing information.
- **Check your configuration**: Use the "Check again" button to verify your configuration.
- **Progress through levels**: Once a level is validated, proceed to the next level.
- **Export configurations**: After successfully completing a level, export the configuration using the "Get my config" button.

### Submission Requirements

For project submission, you must:

1. Complete all 10 levels successfully.
2. Export each level's configuration file using the "Get my config" button.
3. Place all 10 exported configuration files (`level1.json` through `level10.json`) at the root of your repository.
4. Ensure your repository includes this README.md file.

**Repository Structure:**
```
NetPractice/
├── README.md
└── Levels/
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

## Key Networking Concepts

### TCP/IP Addressing

**IPv4 Address Structure**: An IPv4 address consists of 32 bits divided into 4 octets (8 bits each), written in decimal notation separated by dots (e.g., 192.168.1.1). Each octet ranges from 0 to 255.

**IP Address Classes**:
- **Class A**: 1.0.0.0 to 126.255.255.255 (supports ~16 million hosts)
- **Class B**: 128.0.0.0 to 191.255.255.255 (supports ~65,000 hosts)
- **Class C**: 192.0.0.0 to 223.255.255.255 (supports 254 hosts)

**Private IP Ranges** (RFC 1918):
- 10.0.0.0 to 10.255.255.255 (Class A)
- 172.16.0.0 to 172.31.255.255 (Class B)
- 192.168.0.0 to 192.168.255.255 (Class C)

### Subnet Mask

A subnet mask determines which portion of an IP address represents the network and which represents the host. It's used to divide larger networks into smaller subnetworks (subnets).

**CIDR Notation**: Subnet masks can be written in CIDR (Classless Inter-Domain Routing) notation using a slash followed by the number of network bits (e.g., /24).

**Common Subnet Masks**:
| CIDR | Decimal Notation | Usable Hosts | Use Case |
|------|------------------|--------------|----------|
| /30  | 255.255.255.252 | 2 | Point-to-point links |
| /28  | 255.255.255.240 | 14 | Small networks |
| /27  | 255.255.255.224 | 30 | Small office |
| /26  | 255.255.255.192 | 62 | Medium office |
| /25  | 255.255.255.128 | 126 | Large office |
| /24  | 255.255.255.0   | 254 | Standard network |

**Calculating Network Range**:
- **Network Address**: First address in the range (all host bits set to 0)
- **Broadcast Address**: Last address in the range (all host bits set to 1)
- **Usable Hosts**: Total addresses - 2 (network and broadcast addresses)

### Default Gateway

The default gateway is the IP address of a router that serves as an access point to other networks. When a host needs to communicate with a device outside its local subnet, it forwards packets to the default gateway.

**Key Points**:
- Must be on the same subnet as the host
- Typically the first or last usable IP in the subnet
- Essential for inter-network communication

### Routing

Routing is the process of selecting paths in a network along which to send network traffic. Routers use routing tables to determine where to forward packets.

**Routing Table Components**:
- **Destination**: The target network or host
- **Gateway/Next Hop**: The IP address to forward packets to
- **Interface**: The network interface to use

**Route Types**:
- **Default Route** (0.0.0.0/0): Catches all traffic not matching specific routes
- **Specific Routes**: Match particular networks or hosts
- **Static Routes**: Manually configured
- **Dynamic Routes**: Automatically learned through routing protocols

**Route Precedence**: More specific routes (longer prefix length) take priority over less specific routes. For example, a /30 route is more specific than a /24 route.

### Routers and Switches

**Routers**:
- Operate at Layer 3 (Network Layer) of the OSI model
- Forward packets between different networks
- Make decisions based on IP addresses
- Maintain routing tables
- Can connect networks with different subnet masks

**Switches**:
- Operate at Layer 2 (Link Layer) of the OSI model
- Forward frames within the same network
- Make decisions based on MAC addresses
- Create collision domains
- Connect devices in the same subnet

### TCP/IP Layers (Relevant to NetPractice)

1. **Application Layer (Layer 1)**: bridge between your software and the lower layers of the network
2. **Transport Layer (Layer 2)**: responsible for making sure that data is sent reliably and in the correct order between devices
3. **Network Layer (Layer 3)**: responsible for routing data across different networks to ensure it reaches the correct destination
4. **Link Layer (Layer 4)**: used for finding the best path for data to travel across different networks so it can reach the right destination

NetPractice focuses primarily on Layer 3 (Network Layer) concepts, including IP addressing, subnetting, and routing.

## Level Overview

### Levels 1-2: Basic IP Configuration
Introduction to IP addressing with simple point-to-point connections. Focus on understanding how devices on the same subnet communicate directly.

### Levels 3-4: Subnetting Fundamentals
Application of subnet masks to segment networks. Learn to calculate valid IP ranges and understand network boundaries.

### Levels 5-6: Introduction to Routing
Configuration of default gateways and basic routing tables. Understand how packets are forwarded between different networks.

### Levels 7-8: Intermediate Routing
Work with multiple routers and routing tables. Learn about route specificity and how routers make forwarding decisions.

### Levels 9-10: Advanced Network Topologies
Complex scenarios involving multiple networks, routers, and routing paths. Integration of all concepts learned in previous levels.

## Configuration Principles

1. **Same Subnet Communication**: Two devices can communicate directly only if they're on the same subnet (same network portion of their IP addresses).

2. **No IP Conflicts**: Each interface must have a unique IP address within the network.

3. **Valid IP Ranges**: Host IP addresses must fall within the usable range defined by the subnet mask (excluding network and broadcast addresses).

4. **Gateway Accessibility**: A default gateway must be on the same subnet as the host that uses it.

5. **Routing Path Completeness**: For end-to-end communication, there must be a complete routing path from source to destination.

## Resources

### Learning Resources
- [Subnet Calculator](https://www.calculator.net/ip-subnet-calculator.html) - Tool for subnet calculations
- [TCP/IP Guide](https://www.geeksforgeeks.org/computer-networks/tcp-ip-model/) - In-depth TCP/IP protocol documentation
- [Subnet Mask Cheat Sheet](https://www.aelius.com/njh/subnet_sheet.html)

### AI Usage in This Project

**AI Tool Used**:

**Tasks Assisted By AI**:
1. **Documentation Structure**: AI helped organize the README.md following 42 curriculum requirements and best practices for technical documentation.

2. **Concept Explanations**: AI provided clear, accurate explanations of networking concepts (TCP/IP, subnetting, routing, OSI model) with appropriate technical depth for the 42 level.

3. **Table Formatting**: AI generated the subnet mask reference table and formatted it for clarity and easy reference during exercises.

4. **Resource Compilation**: AI helped identify and organize relevant official documentation (RFCs), learning resources, and tutorials appropriate for the NetPractice project scope.

5. **Content Review**: AI assisted in ensuring technical accuracy of networking terminology and concepts presented in the documentation.

**Parts Completed Without AI**:
- All 10 level configurations (level1.json through level10.json) were solved manually
- Practical subnet calculations and IP addressing decisions
- Routing table configurations for each level
- Testing and validation of network configurations

The actual problem-solving and configuration work for NetPractice was completed independently to ensure genuine learning and understanding of networking concepts.

