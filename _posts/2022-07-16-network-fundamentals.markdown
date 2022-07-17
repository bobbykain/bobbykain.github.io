---
layout: post
title:  "Network Fundamentals"
date:   2022-07-16
categories:
---

## **OSI (Open Systems Interconnection) Model**

### Useful references
* [Ed Harmoush - OSI Model](https://www.practicalnetworking.net/series/packet-traveling/osi-model/)<!---https://web.archive.org/web/20220715143928/https://www.practicalnetworking.net/series/packet-traveling/osi-model/-->
* [Godred Fairhurst - OSI Model](https://erg.abdn.ac.uk/users/gorry/course/intro-pages/osi.html)<!---https://web.archive.org/web/20210507061431/https://erg.abdn.ac.uk/users/gorry/course/intro-pages/osi.html-->
* [Godred Fairhurst - Encapsulation](https://erg.abdn.ac.uk/users/gorry/course/intro-pages/encapsulation.html)<!---https://web.archive.org/web/20220716030758/https://erg.abdn.ac.uk/users/gorry/course/intro-pages/encapsulation.html-->

![osi-gif](/assets/img/osi-model/packtrav-encap-decap.gif)
![osi](/assets/img/osi-model/osi.gif)
![osi-encap](/assets/img/osi-model/osi-encapsulation.gif)

--------------------------------------------------------------------------------------------------------------

### **Physical Layer (Layer 1)**
* [Godred Fairhurst - Physical Layer](https://erg.abdn.ac.uk/users/gorry/course/phy-pages/phy.html)<!---https://web.archive.org/web/20210428021349/https://erg.abdn.ac.uk/users/gorry/course/phy-pages/phy.html-->
* Two communicating devices are linked through a physical medium. This physical medium is used to transfer an electrical or optical signal between two directly connected devices.
* Protocol Data Unit: Bit

#### Examples (Media Types)
* Ethernet PHY
* Unshielded Twisted Pair (UTP) cables
* Shielded Twisted Pair (STP) cables
* Coaxial Cable
* Optical Fiber

![physical](/assets/img/osi-model/physical-layer.jpg){:height="49%" width="49%"}

--------------------------------------------------------------------------------------------------------------

### **Datalink Layer (Layer 2)**
* [Godred Fairhurst - Ethernet](https://erg.abdn.ac.uk/users/gorry/course/lan-pages/enet.html)
* The Datalink layer allows two hosts that are directly connected through the physical layer to exchange information.
* Protocol Data Unit: Frame
* Provides Hop-to-Hop Delivery

#### Examples
* HDLC
* Ethernet

#### Ethernet Header
* 14 bytes
* VLAN (802.1Q) Tag is placed between the EtherType/Length field
* 802.1Q Tag EtherType value: 0x8100
* IPv4 EtherType value: 0x0800
* IPv6 EtherType value: 0x86DD
* ARP EtherType value: 0x0806
* MTU (maximum payload): 1500 bytes

![ethernet-header](/assets/img/osi-model/ethernet-header.jpg){:height="75%" width="75%"}
![datalink](/assets/img/osi-model/datalink-layer.jpg){:height="49%" width="49%"}

--------------------------------------------------------------------------------------------------------------

### **Network Layer (Layer 3)**
* [Godred Fairhurst - IP](https://erg.abdn.ac.uk/users/gorry/course/inet-pages/ip.html)
* The Datalink layer allows directly connected hosts to exchange information, but it is often necessary to exchange information between hosts that are not attached to the same physical medium. This is the task of the network layer.
* Protocol Data Unit: Packet
* Provides End-to-End Delivery

#### Examples
* IPv4 (Internet Protocol Version 4)
* IPv6 (Internet Protocol Version 6)
* CLNS (Connectionless-mode Network Service)

#### IPv4 Header
* 20 bytes (minimum) to 60 bytes (maximum)
* Version (IPv4): 0100
* Internet Header Length: 20 bytes to 60 bytes
* Type of Server (aka Differentiated Services Code Point): QoS
* Total Length: Used to denote the size of the entire datagram.
* Identification: The identification or ID field in a packet can identify an IP datagram’s fragments uniquely.
* Flags: Flag in an IPv4 header is a three-bit field that is used to control and identify fragments.
* Fragment Offset: These are used to specify the offset of a fragment relative to the start of the IP datagram, which when it was not fragmented. As you can expect, the first offset of a fragment is always set to zero.
* Time to live: Indicates the maximum time the datagram will be live in the internet system.
* Protocol: Denotes which protocol is used in the later (data) portion of the datagram. For Example, number 6 is used to denote TCP and 17 is used to denote UDP protocol.
* Checksum: Used to check the header for any errors. The header is compared to the value of its checksum at each hop, and in case the header checksum is not matching, the packet is discarded.
* Source Address: 32-bit address of the source of the IPv4 packet.
* Destination Address: 32-bit address of the destination of the IPv4 packet.
* Options: These options contain values and settings for things related to security.
* MTU (datagram size): 20 bytes (minimum) to 64KB/65,536 bytes (maximum)

![network](/assets/img/osi-model/ipv4-header.png)
![network](/assets/img/osi-model/network-layer.jpg){:height="49%" width="49%"}

--------------------------------------------------------------------------------------------------------------

### **Transport Layer (Layer 4)**
* [Godred Fairhurst - Transport](https://erg.abdn.ac.uk/users/gorry/course/inet-pages/transport.html)
* [Godred Fairhurst - TCP](https://erg.abdn.ac.uk/users/gorry/course/inet-pages/tcp.html)
* [Godred Fairhurst - UDP](https://erg.abdn.ac.uk/users/gorry/course/inet-pages/udp.html)
* The network layer enables hosts to reach each others. However, different communication flows can take place between the same hosts. These communication flows might have different needs (some require reliable delivery, other not) and need to be distinguished. Ensuring an identification of a communication flow between two given hosts is the task of the transport layer.
* Protocol Data Unit: Segment (TCP) or Datagram (UDP)
* Provides Service-to-Service Delivery

#### TCP (Transmission Control Protocol)
* Connection Oriented, Reliable
* Flow Controlled
* Header size: 20 bytes (min) to 60 bytes (max)

![tcp-header](/assets/img/osi-model/tcpheader.jpg)

#### UDP (User Datagram Protocol)
* Connectionless, Best Effort
* Reduced Overhead
* 8 byte header
    * Source Port
    * Destination Port
    * UDP length: The number of bytes comprising the combined UDP header information and payload data
    * UDP Checksum: A checksum to verify that the end to end data has not been corrupted by routers or bridges in the network or by the processing in an end system.

![udp-header](/assets/img/osi-model/udp-header.gif)
![peer-layer](/assets/img/osi-model/peer-layer.gif)
![network](/assets/img/osi-model/transport-layer.jpg){:height="49%" width="49%"}
