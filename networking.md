- [To-do](#to-do)
- [Terminology](#terminology)
  - [Client](#client)
  - [Server](#server)
  - [Host](#host)
  - [Packet/Package](#packetpackage)
  - [Frame](#frame)
  - [Bandwidth](#bandwidth)
  - [Throughput](#throughput)
  - [Latency](#latency)
  - [Protocol](#protocol)
  - [IP Address](#ip-address)
  - [Port](#port)
  - [Socket](#socket)
  - [MAC Address](#mac-address)
  - [ARP](#arp)
  - [Transmission Media Types](#transmission-media-types)
  - [DNS Servers](#dns-servers)
    - [Cloudflare](#cloudflare)
  - [Infrastructure](#infrastructure)
    - [Physical infrastructure:](#physical-infrastructure)
    - [Logical infrastructure:](#logical-infrastructure)
  - [Architecture](#architecture)
- [Protocols](#protocols)
  - [Core Protocols](#core-protocols)
    - [TCP](#tcp)
    - [UDP](#udp)
    - [IP](#ip)
    - [ICMP](#icmp)
  - [Application Protocols](#application-protocols)
    - [SSL / TLS](#ssl--tls)
    - [HTTP / HTTPS](#http--https)
    - [WebSocket](#websocket)
    - [SSH](#ssh)
    - [FTP / SFTP](#ftp--sftp)
    - [SMTP / IMAP](#smtp--imap)
    - [DNS](#dns)
    - [DHCP](#dhcp)
    - [NTP](#ntp)
    - [SNTP](#sntp)
- [Networks](#networks)
  - [Network Types](#network-types)
    - [LAN](#lan)
    - [WAN](#wan)
    - [PAN](#pan)
    - [MAN](#man)
    - [VPN](#vpn)
    - [Cloud](#cloud)
    - [Client-Server Network](#client-server-network)
    - [Peer-to-Peer Network](#peer-to-peer-network)
  - [Network Devices](#network-devices)
    - [Router](#router)
    - [Hub](#hub)
    - [Switch](#switch)
    - [Modem](#modem)
    - [Access Point](#access-point)
- [Network Models and Architecture](#network-models-and-architecture)
  - [OSI Model](#osi-model)
    - [1. Physical](#1-physical)
    - [2. Data Link](#2-data-link)
    - [3. Network](#3-network)
    - [4. Transport](#4-transport)
    - [5. Session](#5-session)
    - [6. Presentation](#6-presentation)
    - [7. Application](#7-application)
  - [TCP/IP Model](#tcpip-model)
    - [1. Network Access](#1-network-access)
    - [2. Internet](#2-internet)
    - [3. Transport](#3-transport)
    - [4. Application](#4-application)
  - [Network Architectures](#network-architectures)
    - [Two-Tier](#two-tier)
    - [Three-Tier](#three-tier)
    - [Spine-Leaf](#spine-leaf)
  - [Network Design Principles](#network-design-principles)
  - [Design Best Practices](#design-best-practices)
- [Building a Network](#building-a-network)
  - [IP Addressing](#ip-addressing)
    - [IPv4 vs IPv6](#ipv4-vs-ipv6)
    - [Public vs Private Addresses](#public-vs-private-addresses)
    - [IP vs MAC vs ARP](#ip-vs-mac-vs-arp)
    - [NAT / PAT](#nat--pat)
    - [NAT64](#nat64)
    - [PAT / NAT Overload](#pat--nat-overload)
    - [Static vs Dynamic NAT](#static-vs-dynamic-nat)
  - [Subnetting](#subnetting)
    - [Subnet Masks](#subnet-masks)
    - [CIDR](#cidr)
    - [VLSM](#vlsm)
    - [Supernetting](#supernetting)
  - [Routing](#routing)
    - [Static vs Dynamic Routing](#static-vs-dynamic-routing)
    - [Default Gateway](#default-gateway)
    - [SD-WAN](#sd-wan)
      - [MPLS](#mpls)
    - [VRF](#vrf)
    - [Routing Protocols](#routing-protocols)
- [Resources](#resources)
  - [Overall](#overall)
  - [Network Devices](#network-devices-1)
    - [Modem vs Router](#modem-vs-router)
    - [Hub, Switch and Router](#hub-switch-and-router)


# To-do

- [ ] SAN (Storage Area Network) -> Network Types
- [ ] Include links from roadmaps to useful resources to relevant topics
- [ ] Maybe a FAQ
- [ ] Cisco Packet Tracer - Try it out
- [ ] Classless Inter-Domain Routing (CIDR)

# Terminology

## Client

A client is **any** device or software application that sends requests to a server to access resources or services.

## Server

A server is a **computer** or **software system** that **listens for requests** from clients and **responds** by providing resources, data, or services.

> [!NOTE]
> They are typically designed to be always available, handling multiple client connections at the same time. Servers can host websites, store files, manage emails, or run applications that many users access simultaneously.

## Host

A host is **any** device connected to a network that has an IP address and can send or receive data.

This includes computers, servers, printers, smartphones, and any other networked device. The term is used broadly to refer to **any endpoint that participates in network communication**.

## Packet/Package

In networking, a package or packet is a **small chunk of data broken off from a larger message for transmission across a network**.

Each packet travels independently through the network and is **reassembled** at the destination. Packets contain both the **payload data** and **header information**, such as source and destination addresses, needed to route them correctly.

## Frame

A frame is **a unit of data transmission** at the **Data Link layer of the OSI model**.

It wraps raw bits into a structured format that **includes source** and **destination MAC addresses**, the **data payload**, and **error-checking information**. Frames are used to move data between devices on the **same local network segment**.

## Bandwidth

Bandwidth refers to the **maximum amount of data that can be transmitted** over a network connection **in a given amount of time**, typically measured in bits per second (bps).

> [!NOTE]
> Higher bandwidth means more data can flow simultaneously, which generally results in faster network performance. It is often compared to the width of a pipe: the wider the pipe, the more water (data) can flow through it at once.

## Throughput

Throughput is the **actual amount of data successfully transferred over a network in a given period of time**, as opposed to the theoretical maximum that bandwidth represents.

While bandwidth is the capacity of a network link, throughput reflects real-world performance after accounting for packet loss, latency, and protocol overhead. It is also measured in bits per second.

## Latency

Latency is the **time it takes for a data packet to travel from its source to its destination**, usually measured in milliseconds.

> [!NOTE]
> Low latency means data arrives quickly, which is critical for real-time applications like video calls and online gaming. Latency is influenced by factors such as physical distance, network congestion, and the number of hops between devices.

## Protocol

A protocol is a **set of rules** that defines how data is **formatted**, **transmitted**, and **received** between devices on a network.

> [!NOTE]
> Protocols ensure that different systems, regardless of manufacturer or operating system, can predictably communicate with each other. Examples include TCP, IP, HTTP, and DNS, each governing a specific aspect of how network communication works.

## IP Address

An IP address is a **numerical label assigned to each device** on a network that uses the **Internet Protocol** for communication.

It serves two main purposes: **identifying the host** and **providing its location in the network** for routing purposes. IP addresses come in two versions: **IPv4**, which uses a **32-bit** format, and **IPv6**, which uses a **128-bit** format to accommodate a much larger number of devices.

## Port

A port is a **numerical identifier** used to **direct network traffic to a specific application or service** running on a device.

> [!NOTE]
> While an IP address identifies the device, the port number identifies which program on that device should handle the incoming data. For example, web traffic typically uses port 80 for HTTP and port 443 for HTTPS.

## Socket

A socket is the **combination of an IP address and a port number**, forming a unique endpoint for network communication.

> [!NOTE]
> When two devices establish a connection, each end uses a socket to send and receive data, creating a **two-way communication channel**. Sockets are the fundamental abstraction used by applications to interact with the network.

## MAC Address

A MAC address, or **Media Access Control address**, is a **unique hardware identifier** assigned to a **network interface card (NIC)** by its manufacturer.

It operates at the **Data Link layer** and is **used to identify devices within the same local network segment**. Unlike IP addresses, MAC addresses are typically fixed and do not change as a device moves between networks.

## ARP

ARP, or **Address Resolution Protocol**, is used to **map an IP address to a physical MAC address on a local network**.

> [!NOTE]
> When a device wants to communicate with another device on the same network, it uses ARP to discover which MAC address corresponds to a known IP address. The result is stored temporarily in an ARP cache to speed up future lookups.

## Transmission Media Types

Transmission media refers to **the physical or wireless channels through which data travels between devices**.

> [!NOTE]
> Wired media includes twisted pair cables (like Ethernet), coaxial cables, and fiber optic cables, each with different speeds, ranges, and interference characteristics. Wireless media uses radio waves, microwaves, or infrared signals to transmit data without physical connections.

## DNS Servers

DNS (Domain Name System) servers **translate human-readable domain names into IP addresses** that computers use to find servers on a network.

> [!NOTE]
> **DNS resolver**: Finds the IP address for a domain name by querying other DNS servers if necessary.
>
> **DNS server**: A general term for a server that handles DNS queries. It can provide answers directly or help find them.
>
> **Key distinction**: A resolver finds the answer on your behalf, while an authoritative DNS server stores the official DNS records for a domain.

### Cloudflare

Cloudflare's DNS resolver, known by its address 1.1.1.1, is a public DNS service focused on speed and privacy. It is consistently ranked among the fastest DNS resolvers in the world and does not log user queries for advertising purposes. Cloudflare also supports **DNS over HTTPS (DoH)** and **DNS over TLS (DoT)** to encrypt DNS queries and prevent snooping.

## Infrastructure

**Infrastructure means the underlying components that make something work**. It can include **both physical and logical components**.

### Physical infrastructure:

- Routers
- Switches
- Ethernet cables
- Wi-Fi access points
- Network cards

### Logical infrastructure:

- IP addresses
- Subnets
- VLANs
- Routing rules
- Network configurations

**For example**: LAN is the local network connecting devices, including its physical connections and logical configuration.

**Think of it this way**:

- Infrastructure = What makes the network work.
- Topology = How the network components are connected.
- Subnet = How IP addresses are logically grouped.

> [!NOTE]
> **LAN**: The local network infrastructure.
>
> **Subnet**: A logical division of an IP network.

## Architecture

While infrastructure refers to the underlying components and resources that make a system work, **architecture describes how those components are structured, connected and designed to work together**.

- How routers and switches are connected.
- How networks are divided into subnets.
- How traffic flows between networks.
- Where firewalls are placed.
- How redundancy and failover work.

> [!NOTE]
> **Failover** is the process of automatically switching to a backup system or connection when the primary one fails.

# Protocols

## Core Protocols

### TCP

TCP or **Transmission Control Protocol** sets up a connection between two devices before sending any data, then makes sure every piece of data arrives in order and without errors.

It **splits data into segments**, **numbers them**, and **asks for retransmission if a segment gets lost or corrupted**. Most applications that need reliability, like web browsing, email, or file transfer, run on top of TCP.

### UDP

UDP or **User Datagram Protocol** sends data without setting up a connection first and without checking whether it arrives.

It **skips the overhead of acknowledgments and retransmissions**, which makes it **faster than TCP but less reliable**. Applications like video streaming, online gaming, and DNS lookups use UDP when speed matters more than guaranteed delivery.

### IP

IP or **Internet Protocol** is responsible for addressing and routing packets across networks so they can reach their destination.

It **adds source and destination IP addresses to packets** and **uses routing to determine where to send them next**. IP provides best-effort delivery, meaning it doesn't guarantee that packets arrive, arrive in order, or arrive without errors. Protocols like TCP handle reliability when needed, while UDP sends data without those reliability mechanisms.

### ICMP

ICMP or **Internet Control Message Protocol** carries diagnostic and error messages between devices on a network, rather than application data.

> [!NOTE]
> Routers and hosts use it to report problems like an unreachable destination or an expired packet, and tools like `ping` and `traceroute` rely on it directly. It works at the network layer, alongside IP, but it doesn't transport regular traffic.

## Application Protocols

### SSL / TLS

**SSL (Secure Sockets Layer)** and its successor **TLS (Transport Layer Security)** are **cryptographic protocols** designed to provide secure communication over a network.

They work by **encrypting the data** exchanged between a client and a server, **verifying the identity of the parties** involved through **digital certificates**. TLS is the modern standard and is used to secure HTTPS connections, email, and many other internet services.

### HTTP / HTTPS

**HTTP (HyperText Transfer Protocol)** is the foundation of data communication on the web, **defining how messages are formatted and transmitted between browsers and servers**.

**HTTPS** is the **secure** version of HTTP, adding an **SSL/TLS encryption layer** to protect data from being intercepted during transmission. Most modern websites use HTTPS to ensure privacy and data integrity for their users.

### WebSocket

WebSocket is a **communication protocol** that provides a **persistent, full-duplex connection between a client and a server over a single TCP connection**.

**Full-duplex** means that both sides can send and receive data at the same time.

Unlike traditional HTTP requests where the client must initiate every interaction, **WebSockets allow for continuous, real-time data exchange in both directions once the initial handshake is complete**. This makes it ideal for applications requiring low-latency updates, such as live dashboards, chat systems, and real-time gaming.

### SSH

SSH, or **Secure Shell**, is a **network protocol** that provides a **secure, encrypted channel for remotely accessing and managing devices over an unsecured network**.

> [!NOTE]
> It replaces older, insecure protocols like Telnet by encrypting all communication between the client and the server. Network engineers use SSH extensively to configure routers, switches, and servers from a remote location.

### FTP / SFTP

FTP or **File Transfer Protocol** is a standard protocol **used to transfer files** between a client and a server over a network.

It operates over **two channels** (one for commands and one for data), but transmits information in **plain text**, making it insecure.

SFTP or **SSH File Transfer Protocol** is a secure alternative that **encrypts** both commands and data using SSH, making it the preferred choice for transferring sensitive files.

### SMTP / IMAP

SMTP or **Simple Mail Transfer Protocol** is the protocol used to **send emails** from a client to a server or between mail servers.

IMAP or **Internet Message Access Protocol** is **used by email clients to retrieve and manage messages** stored on a mail server, allowing access from multiple devices while keeping messages synchronized. Together, these protocols handle the sending and receiving sides of email communication.

### DNS

DNS, or **Domain Name System**, is the system that **translates human-readable domain names like `www.example.com` into IP addresses that computers use to identify each other on the network**.

DNS operates as a **distributed, hierarchical database** spread across many servers around the world. Without DNS, users would need to memorize IP addresses to visit websites or access online services.

### DHCP

DHCP, or **Dynamic Host Configuration Protocol**, is a network management protocol that **automatically assigns IP addresses and other network configuration parameters to devices when they join a network**.

> [!NOTE]
> Without DHCP, administrators would need to manually configure the IP address, subnet mask, gateway, and DNS settings on every device. DHCP simplifies network management by handling these assignments dynamically from a central server or router.

### NTP

NTP, or **Network Time Protocol**, is **used to synchronize the clocks of computers and network devices over a network**.

> [!NOTE]
> NTP works by having **devices query time servers and adjust their local clocks to match**, accounting for network delay in the process. Accurate timekeeping is essential for logging events, coordinating distributed systems, and ensuring security certificates work correctly.

### SNTP

SNTP, or **Simple Network Time Protocol**, is a **simplified version of NTP** used to **synchronize device clocks over a network**.

> [!NOTE]
> It is less precise than full NTP but requires fewer resources, making it suitable for devices that do not need highly accurate timekeeping. SNTP is commonly used in **embedded systems**, **IoT devices**, and environments where simplicity is prioritized over precision.

# Networks

A network is a **collection of two or more devices connected to share resources and communicate**.

## Network Types

### LAN

A LAN, or **Local Area Network**, is a network that connects devices within a limited geographic area, such as a home, office, or building.

> [!NOTE]
> LANs typically use Ethernet cables or Wi-Fi to link computers, printers, and other devices, allowing them to share files and resources at high speeds. Because all devices are physically close together, LANs offer **low latency** and **high bandwidth** compared to larger networks.

**-- WLAN --**

A WLAN, or **Wireless Local Area Network**, is a type of LAN that uses wireless radio signals instead of cables to connect devices.

### WAN

A WAN, or **Wide Area Network**, is a network that spans a large geographic area, often connecting multiple LANs across cities, countries, or continents.

> [!NOTE]
> The Internet itself is the largest example of a WAN. Organizations use WANs to connect their branch offices and data centers.

### PAN

A PAN, or **Personal Area Network**, is a small network designed for communication between devices in proximity to a single person, typically within a range of a few meters.

> [!NOTE]
> Examples include connecting a smartphone to wireless earbuds via Bluetooth or linking a laptop to a smartwatch. PANs can be wired (such as USB) or wireless (such as Bluetooth or infrared).

### MAN

A MAN, or **Metropolitan Area Network**, is a network that covers a geographic area roughly the size of a city or a large campus.

> [!NOTE]
> It is **larger than a LAN** but **smaller than a WAN**, often used by organizations or service providers to connect multiple buildings or locations within the same metropolitan region.

### VPN

A VPN, or **Virtual Private Network**, creates an **encrypted tunnel** between a device and a remote network over the public Internet, allowing secure communication as if the device were directly connected to that network.

VPNs mask the user's IP address and encrypt all traffic passing through the tunnel.

> [!NOTE]
> Organizations use VPNs to let remote employees securely access internal resources, while individuals use them for privacy and to bypass geographic content restrictions.

### Cloud

In networking, the cloud refers to a model of **delivering computing resources**, such as servers, storage, databases, and networking, **over the Internet** on a pay-as-you-go basis.

> [!NOTE]
> Rather than owning and maintaining physical infrastructure, organizations can provision and scale resources through cloud providers like AWS, Azure, or Google Cloud. This shifts network design considerations to include connectivity to cloud environments, hybrid architectures, and cloud-native security.

### Client-Server Network

A client-server network is a model where **one or more central servers provide resources or services, and multiple client devices request and consume those resources**.

> [!NOTE]
> The server manages shared resources such as files, databases, or applications, while clients interact with them through the network. This model is widely used in enterprise environments because it centralizes management, improves security, and makes it easier to scale.

### Peer-to-Peer Network

A peer-to-peer (P2P) network is one where **each device**, or **peer**, can act as **both a client and a server**, sharing resources directly with other devices without a central server.

> [!NOTE]
> This model is simpler and cheaper to set up than a client-server network, making it common in small home networks or applications like file sharing. However, P2P networks can be harder to manage and secure as they grow in size.

## Network Devices

### Router

A router is a network device that **forwards data packets between different networks**, **directing traffic based on IP addresses**.

It determines the best path for data to travel from source to destination, making routing decisions using **routing tables** and **protocols**. Routers are what connect your home or office network to the Internet and are essential for communication between separate networks.

### Hub

A hub is a basic network device that connects multiple devices **in a LAN** and **broadcasts incoming data to all connected ports**, regardless of the intended recipient.

This makes hubs simple but inefficient, as all devices receive all traffic, even if it is not meant for them. Hubs have largely been replaced by switches, which are smarter and handle traffic more efficiently.

### Switch

A switch is a network device that connects multiple devices **within the same local network** and **forwards data based on MAC addresses**.

> [!NOTE]
> Unlike a hub, a switch sends data only to the specific device it is intended for, making communication more efficient and reducing unnecessary network traffic. Managed switches offer additional features like VLANs, port security, and traffic monitoring.

### Modem

A modem (**modulator-demodulator**) is a device that **converts digital data from a computer into a format suitable for transmission over a communication medium** such as telephone lines or cable, and vice versa.

It serves as the bridge between your local network and your Internet Service Provider's infrastructure. Modern modems often include router functionality built in, combining both devices into a single unit.

### Access Point

A wireless access point (**AP**) is a device that **creates a wireless local area network**, typically in an office or large building, **by connecting to a wired router or switch and broadcasting a Wi-Fi signal**.

Access points are distinct from routers, they extend the network wirelessly but **do not typically perform routing functions** on their own. Multiple access points can be deployed across a large area to extend wireless coverage and allow devices to roam seamlessly.

# Network Models and Architecture

## OSI Model

The OSI (**Open Systems Interconnection**) model is a **conceptual** framework that **standardizes the functions of a network** into **seven distinct layers**, from physical transmission up to application-level communication.

> [!NOTE]
> It was developed to help different systems and vendors communicate using common standards, making troubleshooting and network design more systematic. Each layer has a specific role and interacts only with the layers directly above and below it.

### 1. Physical

The Physical layer is the first and lowest layer of the OSI model, **responsible for the actual transmission of raw bits over a physical medium** such as copper cables, fiber optics, or radio waves.

It **defines the electrical, mechanical, and timing specifications** for hardware components like network cables, connectors, and network interface cards. Everything at this layer deals with the physical delivery of signals, not their meaning.

### 2. Data Link

The Data Link layer is the second layer of the OSI model, **responsible for node-to-node data transfer and error detection within a single network segment**.

It **organizes raw bits** from the Physical layer **into frames** and **uses MAC addresses to identify devices on the local network**. This layer is divided into **two sublayers**: the **Logical Link Control (LLC)** and the **Media Access Control (MAC)**.

> [!NOTE]
> **Node-to-node** means transferring data from one device to another device on the same local network link.

### 3. Network

The Network layer is the third layer of the OSI model, **responsible for logical addressing and routing data packets between devices across different networks**.

It uses **IP addresses** to determine the best path for data to travel from source to destination. **Routers** operate at this layer, making forwarding decisions based on routing tables and protocols.

### 4. Transport

The Transport layer is the fourth layer of the OSI model, **responsible for end-to-end communication**, **data flow control**, and **error recovery** between **applications on different hosts**.

It breaks data into **segments**, ensures they are delivered reliably and in order, and manages retransmission if packets are lost. The two main protocols at this layer are **TCP**, which provides reliable delivery, and **UDP**, which prioritizes speed over reliability.

### 5. Session

The Session layer is the fifth layer of the OSI model, **responsible for establishing, managing, and terminating communication sessions between applications**.

It handles **synchronization and dialog control**, ensuring that data exchanges are organized and that sessions can be paused and resumed if needed. Examples of protocols operating at this layer include NetBIOS and RPC.

### 6. Presentation

The Presentation layer is the sixth layer of the OSI model, **responsible for translating data between the format used by the application and the format used for network transmission**.

It handles tasks such as **data encryption and decryption**, **compression**, and **character encoding**. This layer ensures that data sent from one system can be read by another, regardless of differences in internal data representation.

### 7. Application

The Application layer is the seventh and **topmost layer** of the OSI model, **where end-user software interacts with the network**.

It **provides network services directly to applications**, enabling functions like web browsing, email, file transfer, and domain name resolution. Protocols such as HTTP, FTP, SMTP, and DNS all operate at this layer.

## TCP/IP Model

The TCP/IP model is a **practical**, **four-layer** framework that describes **how data is transmitted over the Internet and most modern networks**.

Unlike the OSI model's seven layers, the TCP/IP model consolidates functions into four layers: **Network Access**, **Internet**, **Transport**, and **Application**.

### 1. Network Access

The Network Access layer is the lowest layer of the TCP/IP model, **combining the functions of the OSI Physical and Data Link layers**.

It handles how data is **physically** transmitted over the network medium, including **framing**, **MAC addressing**, and **hardware-level error detection**. Ethernet and Wi-Fi protocols operate at this layer.

### 2. Internet

The Internet layer of the TCP/IP model **corresponds to the Network layer of the OSI model** and is **responsible for logical addressing and routing packets across networks**.

The primary protocol at this layer is **IP (Internet Protocol)**, which **assigns addresses to packets** and determines **how** they are routed toward their destination. ICMP and ARP also operate at this layer.

### 3. Transport

The Transport layer of the TCP/IP model is **responsible for end-to-end communication** between **applications on different hosts**.

It **uses TCP** for reliable, ordered delivery and **UDP** for faster, connectionless communication where some data loss is acceptable. **This layer manages segmentation**, **flow control**, and **error handling** to ensure data reaches the correct application.

**Flow control** means controlling how much data a sender transmits so that the receiver isn't overwhelmed.

### 4. Application

The Application layer of the TCP/IP model is the **topmost layer** and **encompasses all the protocols that applications use to communicate over the network**.

It **combines** the functions of the **OSI Session**, **Presentation**, and **Application layers** into one. Protocols like HTTP, DNS, SMTP, FTP, and SSH all operate here, directly serving user-facing applications.

## Network Architectures

### Two-Tier

The two-tier architecture, also called the **collapsed core design**, organizes a network into **two layers**: **the distribution layer** and **the access layer**.

**-- Distribution Layer --**

The **distribution layer handles routing**, **policy enforcement**, and **inter-VLAN communication**.

**-- Access Layer --**

**The access layer connects end devices** like computers, phones, and printers to the network.

> [!NOTE]
> This design is simpler and more cost-effective than three-tier architectures and is well suited for small to medium-sized networks where a dedicated core layer would add unnecessary complexity and cost.

### Three-Tier

The three-tier architecture **organizes a network into three distinct layers**: **the core**, **distribution**, and **access layers**.

**-- Core Layer --**

The **core layer** provides **high-speed backbone connectivity between distribution blocks** and is **optimized purely for fast packet forwarding** with no policy enforcement.

**-- Distribution Layer --**

The **distribution layer** **handles routing**, **filtering**, and **policy** **between the core and access layers**.

**-- Access Layer --**

The **access layer** **connects end-user devices to the network**.

> [!IMPORTANT]
> “High-speed backbone connectivity between distribution blocks” means **connecting different parts of a large network using fast connections**.
> - **Backbone**: The network's main, high-capacity connections.
> - **Connectivity**: The ability for different network parts to communicate.
> - **Distribution blocks**: Groups of switches and routers that serve a particular building, area, or section of the network.

> [!NOTE]
> This design is the traditional standard for large enterprise campus networks where scalability, redundancy, and clear separation of functions are critical.

### Spine-Leaf

Spine-leaf is a **two-tier data center network architecture** designed to provide **consistent**, **low-latency connectivity** between **servers and storage** in modern data centers.

Every leaf switch connects to every spine switch, and no leaf connects directly to another leaf. All traffic between devices on different leaves passes through a spine switch in exactly two hops. This predictable, any-to-any connectivity pattern eliminates the bottlenecks and spanning tree complexity of traditional hierarchical designs, making spine-leaf the dominant architecture for hyperscale data centers, cloud environments, and any network carrying large volumes of east-west traffic between servers.

**East-west traffic** is data moving between servers inside the same data center or network.

## Network Design Principles

Network design principles are the **guidelines** and **frameworks** used to plan and build network infrastructure that is **scalable**, **reliable**, **secure**, and **easy to manage**.

A well-designed network is not just about connecting devices; it is about **making deliberate decisions about topology, redundancy, segmentation, and traffic flow** so the network can grow and adapt over time without requiring a complete rebuild. Understanding design principles allows network engineers to evaluate tradeoffs, justify architectural decisions, and build networks that meet both current needs and future requirements.

1. **Topology** -**how devices are connected**- describes the arrangement of devices and connections in a network.
2. **Redundancy** -**having backups**- means having extra components or connections available if something fails.
3. **Segmentation** —**dividing a network into smaller parts**- means splitting a network into separate sections to improve security, performance, and management.
4. **Traffic flow** -**how data moves through the network**- describes the path data takes from its source to its destination and how that traffic is directed or managed.

## Design Best Practices

Network design best practices are a **set of proven principles** that engineers follow to build networks that are **reliable**, **secure**, and **maintainable** over time.

Key practices include **designing for redundancy at every layer** to eliminate single points of failure, **keeping the design as simple as possible** since complexity increases the chance of misconfiguration and makes troubleshooting harder, **segmenting the network using VLANs and subnets** to limit broadcast domains and contain security incidents, **documenting everything** from IP address assignments to device configurations, and **designing with scalability in mind** so the network can grow without requiring a fundamental redesign.

Following established frameworks like Cisco's PPDIOO (Prepare, Plan, Design, Implement, Operate, Optimize) lifecycle model provides a structured approach to network projects from initial planning through ongoing operation.

# Building a Network

## IP Addressing

IP addressing is the system used to assign **unique numerical identifiers** to devices on a network so they can communicate with each other.

Every device connected to a network needs an IP address, which tells other devices where to send data. IP addresses come in two versions — **IPv4** and **IPv6** — and can be assigned statically by an administrator or dynamically by a DHCP server.

### IPv4 vs IPv6

**IPv4** is the original version of the Internet Protocol, using **32-bit addresses** written in dotted decimal notation (e.g., 192.168.1.1), allowing for about 4.3 billion unique addresses.

**IPv6** was introduced to solve the problem of IPv4 address exhaustion, using **128-bit addresses** written in hexadecimal (e.g., 2001:0db8::1), providing an astronomically larger address space. Beyond address size, IPv6 also introduces improvements in routing efficiency, auto-configuration, and built-in security features.

> [!NOTE]
> Instead of four decimal numbers separated by dots, IPv6 has 8 groups separated by colons.
>
> `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
>
> IPv6 addresses can be shortened by removing leading zeros and replacing consecutive groups of zeros with `::`.
>
> Full:
> `2001:0db8:0000:0000:0000:0000:0000:0001`
>
> Shortened:
> `2001:db8::1`

### Public vs Private Addresses

**Public IP addresses** are **globally unique addresses** assigned by Internet Service Providers and are **reachable over the Internet**. **Private IP addresses** are **reserved for use within local networks** and are **not routable on the public Internet** (ranges like 192.168.x.x, 10.x.x.x, and 172.16.x.x are commonly used internally).

Devices with private addresses access the Internet through a process called **NAT (Network Address Translation)**, which maps multiple private addresses to a single public one.

### IP vs MAC vs ARP

An **IP address** is a logical address used to **identify a device across networks** and is assigned by software, while a **MAC address** is a physical address burned into the network interface hardware, **used for communication within a local network segment**.

**ARP (Address Resolution Protocol)** bridges the two by **resolving a known IP address to its corresponding MAC address** so that data can be delivered on the local network.

**Together, these three concepts work in layers**:
1. IP handles routing across networks
2. MAC handles delivery within a network
3. ARP connects them.

### NAT / PAT

**NAT**, or **Network Address Translation**, is a method used by routers to **map private IP addresses on a local network to a single public IP address** before traffic leaves for the Internet. This allows many devices to share one public IP, which helps conserve the limited pool of available IPv4 addresses.

**PAT**, or **Port Address Translation**, is an **extension of NAT** that also **maps different port numbers to each internal device**, allowing multiple simultaneous connections to be tracked and distinguished even when they all share the same public IP.

### NAT64

**NAT64** is a transition mechanism that **allows IPv6-only devices to communicate with IPv4-only servers and services by translating between the two address formats at the network boundary**.

As the Internet continues its gradual migration from IPv4 to IPv6, NAT64 bridges the gap during the transition period, ensuring that devices operating exclusively on IPv6 networks are not cut off from the large portion of the Internet that still runs on IPv4.

It works in conjunction with **DNS64**, which **synthesizes AAAA (IPv6) records** for destinations that only have A (IPv4) records, allowing IPv6 clients to initiate connections to IPv4 destinations transparently.

> [!NOTE]
> **Synthesizes** means creates something new by combining or transforming existing information.

### PAT / NAT Overload

**PAT**, or **Port Address Translation**, also called **NAT Overload**, is the most common form of NAT used in home and enterprise networks. **It allows many devices with private IP addresses to share a single public IP address simultaneously by tracking each connection using a unique combination of the public IP address and a port number**.

When a device on the internal network initiates a connection, the router assigns it a **unique source port number** and **records the mapping in a translation table**, using that mapping to correctly deliver return traffic back to the right internal device. This is what allows an entire office or household to access the Internet through a single public IP address.

### Static vs Dynamic NAT

**Static NAT** creates a **permanent, one-to-one mapping** between a **specific private IP address and a specific public IP address**, ensuring that a device **always appears on the Internet with the same public IP**. It is commonly used for servers that need to be consistently reachable from outside the network, such as web servers or mail servers hosted internally.

**Dynamic NAT**, on the other hand, **maps** private IP addresses to public IP addresses **from a pool on a first-come, first-served basis**, with no device being guaranteed a specific public IP.

Dynamic NAT is less common than PAT since it still requires one public IP per active connection, but is used in scenarios where full PAT is not suitable.

## Subnetting

**Subnetting is the process of dividing a large network into smaller, more manageable sub-networks called subnets**.

It helps **improve network performance** by **reducing broadcast traffic** and allows organizations to **organize their network logically**, such as separating departments or locations. **Subnetting works by borrowing bits from the host portion of an IP address to create a subnet identifier, controlled by the subnet mask**.

### Subnet Masks

A subnet mask is a **32-bit number used alongside an IP address to determine which portion of the address identifies the network and which portion identifies the individual host**.

It works by applying a bitwise `AND` operation with the IP address to extract the network address. For example, a subnet mask of 255.255.255.0 means the first three octets represent the network and the last octet identifies hosts within that network.

### CIDR

CIDR, or **Classless Inter-Domain Routing**, is a **method of allocating IP addresses and routing** that replaced the older class-based system.

Instead of fixed classes (A, B, C), CIDR uses a slash notation (e.g., 192.168.1.0/24) to indicate how many bits are used for the network portion of the address. This allows for more flexible and efficient use of IP address space and is the standard method used in modern networking.

### VLSM

VLSM, or **Variable Length Subnet Masking**, is a technique that **allows a network to be divided into subnets of different sizes** by using different subnet masks within the same network.

Unlike fixed-length subnetting, where all subnets are the same size, VLSM lets you allocate address space more efficiently based on the actual needs of each subnet. This is especially useful for conserving IP addresses in complex network designs with varying host requirements.

### Supernetting

Supernetting, also known as **route aggregation** or **summarization**, is the **process of combining multiple smaller network routes into a single, larger route advertisement**.

This reduces the size of routing tables and simplifies routing by representing several contiguous subnets as one summary route. It is commonly used in large-scale networks and by ISPs to keep routing tables manageable.

> [!IMPORTANT]
> Supernetting doesn't eliminate the need for detailed routing information. It reduces how much information other routers need to maintain.

> [!NOTE]
> In this context, advertisement means a router telling other routers which networks it knows how to reach.
>
> contiguous - szomszédos/határos

## Routing

### Static vs Dynamic Routing

**Static routing** involves **manually configuring fixed routes** in a router's routing table, which do not change unless an administrator updates them. It is simple and predictable, but **does not adapt automatically** to network changes or failures.

**Dynamic routing uses routing protocols** that allow routers to automatically discover routes, share information with neighboring routers, and adapt to topology changes in real time.

> [!NOTE]
> **Topology** describes how devices and networks are connected to each other.

### Default Gateway

A **default gateway** is the **IP address of the router that a device uses to send traffic destined for networks outside its own local subnet**.

When a device does not have a specific route for a destination, it forwards the packet to the default gateway, which then handles the routing decision. In most home and office networks, the default gateway is the IP address of the local router.

> [!NOTE]
> A default gateway is a piece of hardware that sits between a user's home network and the rest of the internet. In most local networks, the default gateway is the Wi-Fi router. It allows a user to access servers and devices outside of their network — all the traffic they send and receive goes through it. Without a default gateway, browsing the internet would be a much more laborious effort.

### SD-WAN

SD-WAN, or **Software-Defined Wide Area Network**, is a **technology that uses software to centrally manage and optimize how traffic is routed across multiple WAN connections**, such as MPLS, broadband Internet, and 4G/5G links, **based on real-time conditions and application requirements**.

Instead of **rigidly** sending all traffic through a single expensive MPLS circuit, SD-WAN can **intelligently distribute traffic across the best available link** at any given moment, improving performance and reducing costs. It is managed through a **centralized controller** that gives network engineers **visibility and control over the entire WAN from a single interface**, without needing to manually configure each individual device at every site.

#### MPLS

**MPLS (Multiprotocol Label Switching)** is a technology used by network providers to move data efficiently through their networks using labels instead of relying solely on traditional IP address lookups at every router.

> [!NOTE]
> **MPLS circuit** means a connection between locations that uses the provider's MPLS network

### VRF

VRF, or **Virtual Routing and Forwarding**, is a **technology that allows a single physical router to run multiple independent routing tables at the same time**.

Each VRF acts like a completely separate virtual router, meaning **traffic in one VRF is fully isolated from traffic in another, even if they share the same physical hardware**. This is commonly used by service providers to keep customer traffic separate on shared infrastructure, and by enterprises to isolate different departments or network segments on the same device.

### Routing Protocols



# Resources

## Overall

[Homenet](https://www.homenethowto.com/switching/arp-mac-ip/)

## Network Devices

### Modem vs Router

[Modem vs Router - Explained Visually](https://www.youtube.com/watch?v=Mad4kQ5835Y)

### Hub, Switch and Router

[Hub, Switch, & Router Explained Visually](https://www.youtube.com/watch?v=1z0ULvg_pW8)
