# Operating System
## Booting

Booting is the process of starting a computer. It can be initiated by hardware such as a button press or by a software command.

Restarting a computer also is called rebooting, which can be **"hard"**, e.g., after electrical power to the CPU is switched from off to on, or **"soft"**, where the power is not cut.
On some systems, a soft boot may optionally clear RAM to zero. Hard and soft booting can be initiated by hardware such as a button press or a software command.
Booting is complete when the operative runtime system, typically the operating system and some applications, is attained.

## Sequencing of Booting

 1.  **Boot Loader**
 ----
Computers powered by the central processing unit can only execute code found in the system's memory.
Modern operating systems and application program code and data are stored on nonvolatile memories.
When a computer is first powered on, it must initially rely only on the code and data stored in nonvolatile portions of the system's memory.
The operating system is not really loaded at boot time, and the computer's hardware cannot perform many complex systems actions.
The program that starts the chain reaction that ends with the entire operating system being loaded is the boot loader or bootstrap loader.
The boot loader's only job is to load other software for the operating system to start.

2.  **Boot Devices**
---
The boot device is the device from which the operating system is loaded.
A modern PC BIOS (Basic Input/Output System) supports booting from various devices.
These include the local hard disk drive, optical drive, floppy drive, a network interface card, and a USB device.
The BIOS will allow the user to configure a boot order.

If the boot order is set to:
- CD Drive
-  Hard Disk Drive
-  Network

3.  **Boot Sequence**
----
There is a standard boot sequence that all personal computers use.
First, the CPU runs an instruction in memory for the BIOS.
That instruction contains a jump instruction that transfers to the BIOS start-up program.
This program runs a power-on self-test (POST) to check that devices the computer will rely on are functioning properly.
Then, the BIOS goes through the configured boot sequence until it finds a bootable device.
Once BIOS has found a bootable device, BIOS loads the bootsector and transfers execution to the boot sector.
If the boot device is a hard drive, it will be a master boot record (MBR).

The MBR code checks the partition table for an active partition.
If one is found, the MBR code loads that partition's boot sector and executes it.
The boot sector is often operating system specific, and however, in most operating systems,
its main function is to load and execute the operating system kernel, which continues start-up.

## Types of Booting

There are two types of booting in an operating system.

-  **Cold Booting**
----
When the computer starts for the first time or is in a shut-down state and switch on the power button to start the system,
this type of process to start the computer is called cold booting.
During cold booting, the system will read all the instructions from the ROM (BIOS) and the Operating System will be automatically get loaded into the system.
This booting takes more time than Hot or Warm Booting.

- **Warm Booting**
----
Warm or Hot Booting process is when computer systems come to no response or hang state, and then the system is allowed to restart during on condition.
It is also referred to as rebooting.
There are many reasons for this state, and the only solution is to reboot the computer.
The system requires a reboot to set software or hardware configuration changes, or sometimes systems may behave abnormally or may not respond properly.
In such a case, the system has to be a force restart.
Most commonly Ctrl+Alt+Del button is used to reboot the system.
Else, in some systems, the external reset button may be available to reboot the system.

## Booting Process in Operating System

1.  **POST**
----
Once the computer system is turned on,
BIOS (Basic Input /Output System) performs a series of activities or functionality tests on programs stored in ROM,
called on POST (Power-on Self Test) that checks to see whether peripherals in the system are in perfect order or not.

2. **CMOS**
---
After the BIOS is done with pre-boot activities or functionality test, it read bootable sequence from CMOS (Common Metal Oxide Semiconductor)
and looks for master boot record in the first physical sector of the bootable disk as per boot device sequence specified in CMOS.

3. **Bootstrap Loader**
---
If the system cannot read the master boot record from any of these sources, ROM displays "No Boot device found" and halted the system.
On finding the master boot record from a particular bootable disk drive,
the operating system loader, also called Bootstrap loader, is loaded from the boot sector of that bootable drive· into memory.
A bootstrap loader is a special program that is present in the boot sector of a bootable drive.

4. **IO.SYS and MSDOS.SYS**
---
The bootstrap loader first loads the IO.SYS file.
After this, MSDOS.SYS file is loaded, which is the core file of the DOS operating system.

5.  **CONFIG.SYS**
----
After this, MSDOS.SYS file searches to find Command Interpreter in CONFIG.SYS file, and when it finds, it loads into memory.
If no Command Interpreter is specified in the CONFIG.SYS file, the COMMAND.COM file is loaded as the default Command Interpreter of the DOS operating system.

6. **AUTOEXEC.BAT**
---
The last file is to be loaded and executed is the AUTOEXEC.BAT file that contains a sequence of DOS commands.
After this, the prompt is displayed.
We can see the drive letter of bootable drive displayed on the computer system,
which indicates that the operating system has been successfully on the system from that drive.

![[bootSequence.png]]
## Dual boot

When two operating systems are installed on the computer system, then it is called dual booting.
Multiple operating systems can be installed on such a system.

Once loaded, it can boot one of the operating systems available on the disk.
The disk can have multiple partitions, each containing a different type of operating system.

When a computer system turns on, a boot manager program displays a menu, allowing the user to choose the operating system to use.

## Types of file system

- **FAT32**
---
FAT32 is an older Windows file system, but it's still used on removable media devices -- just the smaller ones, though.
You'll only want to use this with small storage devices or for compatibility with other devices like digital cameras, game consoles, set-top boxes, and other devices that just support FAT32 and not the newer NTFS file system.

- **NTFS**
---
Modern versions of Windows -- since Windows XP -- use the NTFS file system for their system partition.
External drives can be formatted with either FAT32 or NTFS.

- **HFS+**
----
Macs use HFS+ for their internal partitions, and they like to format external drives with HFS+ too -- this is required to use an external drive
with Time Machine so file system attributes can be properly backed up,

- **Ext2/Ext3/Ext4**
----
You'll often see the Ext2, Ext3, and Ext4 file systems on Linux.
Ext2 is an older file systems, and it lacks important features like journaling
-- if the power goes out or a computer crashes while writing to an ext2 drive, data may be lost.
Ext3 adds these robustness features at the cost of some speed.
Ext4 is more modern and faster -- it's the default file system on most Linux distributions now, and is faster.

- **Btrfs**
---
Btrfs -- "better file system" -- is a newer Linux file system that's still in development.
It isn't the default on most Linux distributions at this point, but it will probably replace Ext4 one day.
The goal is to provide additional features that allow Linux to scale to larger amounts of storage.

- **Swap**
---
On Linux, the "swap" file system isn't really a file system.
A partition formatted as "swap" can just be used as swap space by the operating system

## Create bootable pen-drive

A Bootable USB is a disk that is used to boot up a system for the installation of an Operating System.

Steps to Create a Bootable Windows/Linux USB Using CMD
- <u>Step 1</u>: Run the Command Prompt in Administrator mode.
    There are two ways to do the same:
    - Search for CMD in the Start menu, right-click on the command prompt, and click on Run as Administrator.
    - Open Task Manager, go to File -> Run new task, search for CMD and press enter.

- <u>Step 2</u>: Connect the USB Device to the computer that is to be made bootable.
- <u>Step 3</u>: Type the command diskpart and then press Enter.
- <u>Step 4</u>: Type the command list disk to display a list of all the available storage devices on your system. Press Enter to continue.
- <u>Step 5</u>: Select the disk that is your pen drive. To choose the disk, type the command select disk X in this case, select disk 1 and press Enter.
- <u>Step 6</u>: To make a pendrive bootable, there is a need to format it to clean the existing data. This can be done by the use of clean commands.
- <u>Step 7</u>: Type the command create partition primary and press Enter. This will make the disk primary and ready to be made bootable.
- <u>Step 8</u>: To choose the partition created as primary, type the command select partition 1, and press Enter.
- <u>Step 9</u>: Before making the disk bootable, you need to format it as NTFS if you are using legacy BIOS.
    This can be done with the use of a command format fs=ntfs quick and press Enter.
- <u>Step 10</u>: Type the command active and press Enter. This will mark the primary bootable partition as Active.
- <u>Step 11</u>: Type the command exit to exit DISKPART and press Enter. Now close the command prompt window.
- <u>Step 12</u>: Now copy all the data from the OS(Windows/Linux/etc.) installation disk to your USB drive that is just been made bootable.
- <u>Step 13</u>:Boot your device from USB
	- Reboot your device.
    - Plug the bootable USB drive you created into the device you want to boot.
    - Turn on your device and use the UEFI menu to boot from the USB drive. The device should boot into Factory OS.
    - Complete the installisation from their installation menu



# Networking
## address

| Basics for comparison                                      | Physical Address                                                                                          | Logical Address                                                                                               |
| ---------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Definition                                                 | The physical address is a location of memory/storage.                                                     | Logical addresses are generated by the CPU.                                                                   |
| Generated By                                               | The physical address is generated by MUM (Memory management unit)                                         | The logical address is generated by the CPU (Central processor unit).                                         |
| Accessed By                                                | Users cannot access physical addresses directly. It uses a logical address to access physical addresses.  | Users can access logical addresses directly. It is used to access physical addresses.                         |
| Space for Address                                          | A set of the physical address is mapped into the logical address and is considered as a physical address. | CPU generates a set of the logical address corresponding to programs are considered as logical address space. |
| Visibility                                                 | It is not visible to the user. Users cannot view the physical address.                                    | It is visible to the user. Users can view logical addresses easily.                                           |
| Variation                                                  | There is only one physical address for one device. Physical addresses are constant.                       | The logical addresses can be varied. There are variations for the logical address.                            |
| Access to Change                                           | A physical address cannot change.                                                                         | The logical address can be change.                                                                            |
| Uses                                                       | It is used to find the physical location of the memory.                                                   | It is used to view the physical address.                                                                      |
| Time for compilation and load time address binding schemes | Same as Logical addresses.                                                                                | Same as Physical addresses.                                                                                   |

# IP
IP Address or Internet Protocol Address is a type of address that is required to communicate one computer with another computer

Classification of IP Address
----
An IP Address is basically classified into two types:

- **Public IP address**
---
A public IP address is an Internet Protocol address, encrypted by various servers/devices
A public Internet Protocol address is an Internet Protocol address accessed over the Internet.
The public Internet Protocol address is a different international Internet Protocol address assigned to a computer device.
The web server, email server, and any server device that has direct access to the Internet are those who will enter the public Internet Protocol address.
Internet Address Protocol is unique worldwide and is only supplied with a unique device.

- **Private IP address**
---
Everything that connects to your Internet network has a private IP address.
Your router generates private IP addresses that are unique identifiers for each device that separates the network.

- **Static IP Address**
---
These are stated as permanent internet addresses.
Mostly these are used by the DNS (Domain Name System) Servers.
The Static IP address does not change but can be changed as part of normal network management.
Static IP addresses are incompatible, given once, remain the same over the years.
This type of IP also helps you get more information about the device.

- **Dynamic IP address**
---
It means constant change.
A dynamic IP address changes from time to time and is not always the same.
Internet Service Providers provide customers with dynamic IP addresses because they are too expensive.
Instead of one permanent IP address, your IP address is taken out of the address pool and assigned to you.
After establishing a connection of a smartphone or computer with the Internet, ISP provides an IP Address to the device, these random addresses are called Dynamic IP Address.
Dynamic IP address will be provided by the Dynamic Host Configuration Protocol (DHCP) server, which can change.

Difference between Private IP and Public IP
---

| Private IP Address                                                                           | Public IP Address                                                        |
| -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| The scope of Private IP is local.                                                            | The scope of Public IP is global.                                        |
| It is used to communicate within the network.                                                | It is used to communicate outside the network.                           |
| Private IP addresses of the systems connected in a network differ in a uniform manner.       | Public IP may differ in a uniform or non-uniform manner.                 |
| It works only on LAN.                                                                        | It is used to get internet service.                                      |
| It is used to load the network operating system.                                             | It is controlled by ISP.                                                 |
| It is available free of cost.                                                                | It is not free of cost.                                                  |
| Private IP can be known by entering “ipconfig” on the command prompt.                        | Public IP can be known by searching “what is my ip” on Google.           |
| Range: 10.0.0.0 – 10.255.255.255, 172.16.0.0 – 172.31.255.255, 192.168.0.0 – 192.168.255.255 | Range: Besides private IP addresses, the rest are public.                |
| Example: 192.168.1.10                                                                        | Example: 17.5.7.8                                                        |
| Private IP uses numeric code that is not unique and can be used again                        | Public IP uses a numeric code that is unique and cannot be used by other |
| Private IP addresses are secure                                                              | The public IP address has no security and is  subjected to attack        |
| Private IP addresses require NAT to communicate with devices                                 | Public IP does not require a network translation                         |

## Version of IP

- I**PV4 (Internet Protocol Version 4)**
---
It is the first version of Internet Protocol address.
The address size of IPV4 is 32 bit number.
In this Internet Protocol Security (IPSec) with respect to network security is optional.
It is having 4,294,967,296 number of address still we are seeing a shortage in network addresses as the use of network & virtual devices are increasing rapidly.

- **IPV6 (Internet Protocol Version 6)**
---
It is the recent version of Internet Protocol address.
The address size of IPV6 is 128 bit number.
In this Internet Protocol Security (IPSec) with respect to network security is mandatory.
It allows 3.4 x 10^38 unique IP addresses which seems to be more than sufficient to support trillions of internet devices present now or coming in future.

## IP address structure

IP addresses are displayed as a set of four digits- the default address may be 192.158.1.38. Each number on the set may range from 0 to 255.
Therefore, the total IP address range ranges from 0.0.0.0 to 255.255.255.255

- **Network ID**
---
It is the part of the left-hand IP address that identifies the specific network where the device is located.
In the normal home network, where the device has an IP address 192.168.1.32, the 192.168.1 part of the address will be the network ID.
It is customary to fill in the last part that is not zero, so we can say that the device’s network ID is 192.168.1.0.

- **Hosting ID**
---
The host ID is part of the IP address that was not taken by the network ID.
Identifies a specific device (in the TCP / IP world, we call devices “host”) in that network.
Continuing with our example of the IP address 192.168.1.32, the host ID will be 32- the unique host ID on the 192.168.1.0 network.


![[ip_header.jpg]]

## Types of Website IP address:
Website IP address is of two types- Dedicated IP Address and Shared IP Address

- **Dedicated IP address**
----
A dedicated IP address is one that is unique for each website.
This address is not used by any other domain.
It provides increased speed when the traffic load is high and brings in increased security.
But dedicated IPs are costly as compared to shared IPs.

- **Shared IP address**
----
A shared IP address is one that is not unique.
It is shared between multiple domains.

## IP Address Classification Based on Operational Characteristics

According to operational characteristics, IP address is classified as follows:

- **Broadcast addressing**
----
The term ‘Broadcast’ means to transmit audio or video over a network.
A broadcast packet is sent to all users of a local network at once.
They do not have to be explicitly named as recipients.
The users of a network can open the data packets and then interpret the information, carry out the instructions or discard it.
This service is available in IPv4.
The IP address commonly used for broadcasting is 255.255.255.255

- **Unicast addressing**
----
This address identifies a unique node on the network.
Unicast is nothing but one-to-one data transmission from one point in the network to another.
It is the most common form of IP addressing.
This method can be used for both sending and receiving data.
It is available in IPv4 and IPv6.

- **Multicast IP addresses**
----
These IP addresses mainly help to establish one-to-many communication.
Multicast IP routing protocols are used to distribute data to multiple recipients.
The class D addresses (224.0.0.0  to  239.255.255.255) define the multicast group.

- **Anycast addressing**
----
In anycast addressing the data, a packet is not transmitted to all the receivers on the network.
When a data packet is allocated to an anycast address, it is delivered to the closest interface that has this anycast address.

## Classful IP Addressing

Classful addressing is network addressing the Internet’s architecture
This addressing method divides the IP address into five separate classes based on four address bits.
Here, classes A, B, C offers addresses for networks of three distinct network sizes.
Class D is only used for multicast, and class E reserved exclusively for experimental purposes.

- **Class A Network**
----
This IP address class is used when there are a large number of hosts.
In a Class A type of network, the first 8 bits (also called the first octet) identify the network, and the remaining have 24 bits for the host into that network.
An example of a Class A address is 102.168.212.226. Here, “102” helps you identify the network and 168.212.226 identify the host.
Class A addresses 127.0.0.0 to 127.255.255.255 cannot be used and is reserved for loopback and diagnostic functions.

- **Class B Network**
----
In a B class IP address, the binary addresses start with 10.
In this IP address, the class decimal number that can be between 128 to 191.
The number 127 is reserved for loopback, which is used for internal testing on the local machine.
The first 16 bits (known as two octets) help you identify the network. The other remaining 16 bits indicate the host within the network.
An example of Class B IP address is 168.212.226.204, where *168 212* identifies the network and *226.204* helps you identify the Hut network host.

- **Class C Network**
----
Class C is a type of IP address that is used for the small network.
In this class, three octets are used to indent the network. This IP ranges between 192 to 223.
The first two bits are set to be 1, and the third bit is set to 0, which makes the first 24 bits of the address them and the remaining bit as the host address.
Mostly local area network used Class C IP address to connect with the network.
Example :192.168.178.1

- **Class D Network**
---
Class D addresses are only used for multicasting applications.
Class D is never used for regular networking operations.
This class addresses the first three bits set to “1” and their fourth bit set to use for “0”.
Class D addresses are 32-bit network addresses.
All the values within the range are used to identify multicast groups uniquely.
Therefore, there is no requirement to extract the host address from the IP address, so Class D does not have any subnet mask.
Example:227.21.6.173

- **Class E Network**
----
Class E IP address is defined by including the starting four network address bits as 1, which allows you two to incorporate addresses from 240.0.0.0 to 255.255.255.255.
However, E class is reserved, and its usage is never defined.
Therefore, many network implementations discard these addresses as undefined or illegal.
Example: 243.164.89.28


![[classful_IP.jpg | 500]]

Bandwidth vs Speed
----

| Bandwidth                                                                                 | Speed                                                                             |
| ----------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Bandwidth refers to the amount of data that may be transferred in a given amount of time. | The term “speed” refers to how quickly something is completed.                    |
| It does not depend on download speed, upload speed, and latency                           | It depends on download speed, upload speed, and latency                           |
| Unit of measurement is in bits per second (bps) or hertz (Hz)                             | Internet speed is measured in megabits per second, Mbps.                          |
| Always higher than speed                                                                  | Speed can never be higher than bandwidth.                                         |
| Bandwidth is the capacity available for use in data transmission                          | Speed is the data transferring rate.                                              |
| Bandwidth is used to refer to the performance of the system or the internet.              | Speed is commonly determined by the physical signaling of the underlying network. |

# Networking device

Physical devices that allow hardware on a computer network to communicate and interact with one another.


- **Repeater**
---
A repeater operates at the physical layer.
Its job is to regenerate the signal over the same network before the signal becomes too weak or corrupted.
They not only amplify the signal but also regenerate it.
It is a 2-port device.

- **Hub**
---
A hub is a basically multi-port repeater.
A hub connects multiple wires coming from different branches,
Hubs cannot filter data, so data packets are sent to all connected devices.
they do not have the intelligence to find out the best path for data packets which leads to inefficiencies and wastage.

Types of Hub
1.  Active Hub
2.  Passive Hub
3. Intelligent Hub

-  **Bridge**
----

A bridge operates at the data link layer.
A bridge is a repeater, with add on the functionality of filtering content by reading the MAC addresses of the source and destination.
It has a single input and single output port, thus making it a 2 port device.

Types of Bridges
1. Transparent Bridges
2. Source Routing Bridges

- **Switch**
---
A switch is a multiport bridge with a buffer and a design that can boost its efficiency(a large number of ports imply less traffic) and performance.
A switch is a data link layer device.
The switch divides the collision domain of hosts, but the broadcast domain remains the same.

Types of  Switch
1. Unmanaged switches
2.  Managed switches
3.  Smart switches
4.  Layer 2 switches
5.  Layer 3 switches
6.  PoE switches
7.  Gigabit switches
8. Rack-mounted switches
9.  Desktop switches
10.  Modular switches

- **Routers**
---
A router is a device like a switch that routes data packets based on their IP addresses.
The router is mainly a Network Layer device.
The router divides the broadcast domains of hosts connected through it.

- **Gateway**
---
A gateway, as the name suggests, is a passage to connect two networks that may work upon different networking models.
They work as messenger agents that take data from one system, interpret it, and transfer it to another system.
Gateways are also called protocol converters and can operate at any network layer.
Gateways are generally more complex than switches or routers.
A gateway is also called a protocol converter.

- **Brouter**
---
It is also known as the bridging router is a device that combines features of both bridge and router.
It can work either at the data link layer or a network layer.
It is capable of routing packets across networks and working -> router
It is capable of filtering local area network traffic. -> bridge

- **NIC**
----
NIC or network interface card is a network adapter that is used to connect the computer to the network.
It is installed in the computer to establish a LAN.
It has a unique id that is written on the chip and it has a connector to connect the cable to it.
The cable acts as an interface between the computer and the router or modem.
NIC card is a layer 2 device which means that it works on both the physical and data link layers of the network model.

![[Networking-Devices.jpg | 500 ]]

## Topology

In Computer Network ,there are various ways through which different components are connected to one another.
Network Topology is the way that defines the structure, and how these components are connected to each other.

The arrangement of a network that comprises nodes and connecting lines via sender and receiver is referred to as Network Topology.
The various network topologies are:

- **Point to Point Topology**
---
Point-to-Point Topology is a type of topology that works on the functionality of the sender and receiver.
It is the simplest communication between two nodes, in which one is the sender and the other one is the receiver.
Point-to-Point provides high bandwidth.

- **Mesh Topology**
----
In a mesh topology, every device is connected to another device via a particular channel.
In Mesh Topology, the protocols used are AHCP (Ad Hoc Configuration Protocols), DHCP (Dynamic Host Configuration Protocol), etc.

- **Star Topology**
---
In Star Topology, all the devices are connected to a single hub through a cable.
This hub is the central node and all other nodes are connected to the central node.
The hub can be passive in nature i.e., not an intelligent hub such as broadcasting devices, at the same time the hub can be intelligent known as an active hub.
Active hubs have repeaters in them.
Coaxial cables or RJ-45 cables are used to connect the computers.
In Star Topology, many popular Ethernet LAN protocols are used as CD(Collision Detection), CSMA (Carrier Sense Multiple Access), etc.

- **Bus Topology**
 ---
Bus Topology is a network type in which every computer and network device is connected to a single cable.
It is bi-directional.
It is a multi-point connection and a non-robust topology because if the backbone fails the topology crashes.
In Bus Topology, various MAC (Media Access Control) protocols are followed by LAN Ethernet connections like TDMA, Pure Aloha, CDMA, Slotted Aloha, etc.

- **Ring Topology**
-----
In a Ring Topology, it forms a ring connecting devices with exactly two neighbouring devices.
A number of repeaters are used for Ring topology with a large number of nodes, because if someone wants to send some data to the last node in the ring topology with 100 nodes, then the data will have to pass through 99 nodes to reach the 100th node.
Hence to prevent data loss repeaters are used in the network.
The data flows in one direction, i.e. it is unidirectional, but it can be made bidirectional by having 2 connections between each Network Node, it is called Dual Ring Topology.
In-Ring Topology, the Token Ring Passing protocol is used by the workstations to transmit the data.

- **Tree Topology**
----
This topology is the variation of the Star topology. This topology has a hierarchical flow of data.
In Tree Topology, protocols like DHCP and SAC (Standard Automatic Configuration ) are used.

- **Hybrid Topology**
----
Hybrid Topology is used when the nodes are free to take any form.
It means these can be individuals such as Ring or Star topology or can be a combination of various types of topologies seen above.
Each individual topology uses the protocol that has been discussed earlier.

![[topology.png]]

## Cloud Computing
Cloud computing is the on-demand access of computing resources—physical servers or virtual servers, data storage, networking capabilities, application development tools, software, AI-powered analytic tools and more—over the internet with pay-per-use pricing.

Famous cloud examples:

- Adobe Creative Cloud
- Amazon Web Services
- Google Cloud
- IBM Cloud
- Microsoft Azure
- OpenStack
- Oracle Cloud
- Panorama9

## Cloud computing components

- **Data centres**
----
CSPs own and operate remote data centres that house physical or bare metal servers,
cloud storage systems and other physical hardware that create the underlying infrastructure and provide the physical foundation for cloud computing.

- **Networking capabilities**
----

Typically, an internet connection known as a wide-area network (WAN) connects front-end users with back-end functions
Other advanced cloud computing networking technologies, including load balancers, content delivery networks (CDNs) and software-defined networking (SDN),
are also incorporated to ensure data flows quickly, easily and securely between front-end users and back-end resources.

- **Virtualization**
----
A single hardware server can be divided into multiple virtual servers.
Virtualization enables cloud providers to make maximum use of their data centre resources.

## Cloud computing services

- **IaaS (Infrastructure-as-a-Service)**
----
IaaS (Infrastructure-as-a-Service) provides on-demand access to fundamental computing resources—physical and virtual servers, networking and storage—over the internet
on a pay-as-you-go basis.
IaaS enables end users to scale and shrink resources on an as-needed basis, reducing the need for high up-front capital expenditures or unnecessary on-premises
or "owned" infrastructure and for overbuying resources to accommodate periodic spikes in usage.

- **PaaS (Platform-as-a-Service)**
----
PaaS (Platform-as-a-Service) provides software developers with an on-demand platform—hardware, complete software stack, infrastructure and development tools—for running,
developing and managing applications without the cost, complexity and inflexibility of maintaining that platform on-premises.
With PaaS, the cloud provider hosts everything at their data center.
These include servers, networks, storage, operating system software, middleware and databases.
PaaS is typically built around containers, a virtualized compute model one step removed from virtual servers.
Containers virtualize the operating system, enabling developers to package the application with only the operating system services it needs to run on any platform
without modification and the need for middleware.
Red Hat® OpenShift® is a popular PaaS built around Docker containers and Kubernetes,

- **SaaS (Software-as-a-Service)**
-----
SaaS (Software-as-a-Service), also known as cloud-based software or cloud applications, is application software hosted in the cloud.
Users access SaaS through a web browser, a dedicated desktop client or an API that integrates with a desktop or mobile operating system.
Cloud service providers offer SaaS based on a monthly or annual subscription fee.
They may also provide these services through pay-per-usage pricing.

- **Serverless computing**
-----
Serverless computing, or simply serverless, is a cloud computing model that offloads all the back-end infrastructure management tasks,
including provisioning, scaling, scheduling and patching to the cloud provider.
This frees developers to focus all their time and effort on the code and business logic specific to their applications.
Moreover, serverless runs application code on a per-request basis only and automatically scales the supporting infrastructure up and down
in response to the number of requests.
With serverless, customers pay only for the resources used when the application runs; they never pay for idle capacity.

- **FaaS**
-----
or Function-as-a-Service, is often confused with serverless computing when, in fact, it’s a subset of serverless.
FaaS allows developers to run portions of application code (called functions) in response to specific events.
Everything besides the code—physical hardware, virtual machine (VM) operating system and web server software management—is provisioned
automatically by the cloud service provider in real-time as the code runs and is spun back down once the execution is complete.
Billing starts when execution starts and stops when execution stops.

![[CloudService.png | 400]]

![[comparisonServices.png]]

## Types of cloud computing

- **Public cloud**
----
A public cloud is a type of cloud computing in which a cloud service provider makes computing resources available to users over the public internet.
These include SaaS applications, individual virtual machines (VMs), bare metal computing hardware, complete enterprise-grade infrastructures and development platforms.
These resources might be accessible for free or according to subscription-based or pay-per-usage pricing models.
The public cloud provider owns, manages and assumes all responsibility for the data centres, hardware and infrastructure on which its customers’ workloads run.
It typically provides high-bandwidth network connectivity to ensure high performance and rapid access to applications and data.
Public cloud is a multi-tenant environment where all customers pool and share the cloud provider’s data centre infrastructure and other resources.
In the world of the leading public cloud vendors, such as Amazon Web Services (AWS), Google Cloud, IBM Cloud®, Microsoft Azure and Oracle Cloud, these customers can number
in the millions.

- **Private cloud**
-----
A private cloud is a cloud environment where all cloud infrastructure and computing resources are dedicated to one customer only.
Private cloud combines many benefits of cloud computing—including elasticity, scalability and ease of service delivery—with the access control, security and resource customization of on-premises infrastructure.
A private cloud is typically hosted on-premises in the customer’s data centre.
However, it can also be hosted on an independent cloud provider’s infrastructure or built on rented infrastructure housed in an offsite data centre.
Many companies choose a private cloud over a public cloud environment to meet their regulatory compliance requirements.
Entities like government agencies, healthcare organizations and financial institutions often opt for private cloud settings for workloads that
deal with confidential documents, personally identifiable information (PII), intellectual property, medical records, financial data or other sensitive data.
By building private cloud architecture according to cloud-native principles, an organization can quickly move workloads to a public cloud or run them within
a hybrid cloud (see below) environment whenever ready.

- **Hybrid cloud**
-----
A hybrid cloud is just what it sounds like: a combination of public cloud, private cloud and on-premises environments.
Specifically (and ideally), a hybrid cloud connects a combination of these three environments into a single, flexible infrastructure for
running the organization’s applications and workloads.
a hybrid cloud environment is ideal for DevOps and other teams to develop and test web applications.
This frees organisations from purchasing and expanding the on-premises physical hardware needed to run application testing, offering faster time to market.

- **Multi-cloud**
----
Multi-cloud uses two or more clouds from two or more different cloud providers.
A multi-cloud environment can be as simple as email SaaS from one vendor and image editing SaaS from another.
But when enterprises talk about multi-cloud, they typically refer to using multiple cloud services—including SaaS, PaaS and IaaS
services—from two or more leading public cloud providers.
Organisations choose multi-cloud to avoid vendor lock-in, to have more services to select from and to access more innovation.
With multi-cloud, organisations can choose and customise a unique set of cloud features and services to meet their business needs.


# Hypervisor

A hypervisor, also known as a Virtual Machine Monitor (VMM),
is a software or hardware component that allows multiple operating systems to share a single physical host computer.

- **Type 1 Hypervisor (Bare-Metal)**
----
Installed directly on the physical hardware, managing and allocating resources to virtual machines.
Examples include VMware ESXi, Microsoft Hyper-V Server, and Xen.

![[VM1.png | 500]]

- **Type 2 Hypervisor (Hosted)**
-----
Runs on top of an existing operating system and enables the creation of virtual machines.
Examples include VMware Workstation, Oracle VirtualBox, and Microsoft Hyper-V (when installed on Windows).

- <b><u>Benefits of hypervisor</u></b>

    - **Server Consolidation**: Efficiently run multiple virtual machines on a single physical server, optimising resource utilisation.
    - **Isolation**: Improved security and stability by isolating virtual machines from each other.
    - **Flexibility**: Easily move and replicate virtual machines across different physical hosts.
    - **Resource Management**: Efficiently allocate and manage resources among virtual machines based on demand.

![[VM2.png | 500]]
Virtual Machine
---
A Virtual Machine is a software that creates a virtualisation environment between the computer platform and the end user in which the end user can operate software.

Virtual Machine Monitor
---
The host software that provides virtualisation is often referred to as a virtual machine monitor (VMM) or hypervisor.
The VMM gives each virtual machine an illusion of a complete computer to itself.

- **Features**
----

Each virtual machine has its own set of virtual hardware (e.g., RAM, CPU, NIC, etc.) upon which an operating system and applications are loaded.
The operating system sees a consistent, normalised set of hardware regardless of the actual physical hardware components.

- **Benefits of VMM**
----
- <u>Partitioning</u>:
    Multiple applications and operating systems can be supported within single physical system.
    There is no overlap amongst memory as each Virtual Memory has its own memory space.
 - <u>Isolation</u>:
    Virtual machines are completely isolated from the host machine and other virtual machines.
    If a virtual machine crashes, all others are unaffected.
    Data does not leak across virtual machines.

# UNIX

GNU/Linux is a Unix-like operating system made up of different OS components and services that create the Linux OS.
GNU stands for GNU's not Unix, which makes the term a recursive acronym, or an acronym in which one of the letters stands for the acronym itself.
The GNU Project initially created most of the components and services used in GNU/Linux and later added the Linux kernel to create the GNU/Linux OS.
The Linux kernel is the core component of GNU/Linux, as it provides basic services and allocates OS resources.
Although there are numerous distributions, Debian, Fedora and Ubuntu are three user-friendly examples of GNU/Linux desktop distributions.

Benefits
---
- <b><u>Software customisation.</u></b>
    Users can customise the OS' software to their liking.
    shell, as it is an outer layer of the OS.
    command-line shells, are programs that enable them to process or give commands to a computer program in text.
 - <b><u>Stability</u></b>
    The OS is stable, as it rarely crashes.
 - <b><u>Open standards</u></b>
    GNU/Linux integrates with other open source platforms, as it supports open
- <b><u>Community</u></b>
    The GNU/Linux user base is a wide and varying group that can create, distribute and help support software.
 - <b><u>Transparency</u></b>
    Users can study the source code, as well as modify and share it. Distributions are also developed in the open.

## CLI

| Linux Commands | Functions                                                                     |
| -------------- | ----------------------------------------------------------------------------- |
| ls             | Displays information about files in the current directory.                    |
| pwd            | Displays the current working directory.                                       |
| mkdir          | Creates a directory.                                                          |
| cd             | To navigate between different folders.                                        |
| rmdir          | Removes empty directories from the directory lists.                           |
| cp             | Moves files from one directory to another.                                    |
| mv             | Rename and Replace the files                                                  |
| rm             | Delete files                                                                  |
| uname          | Command to get basic information about the OS                                 |
| locate         | Find a file in the database.                                                  |
| touch          | Create empty files                                                            |
| ln             | Create shortcuts to other files                                               |
| cat            | Display file contents on terminal                                             |
| ps             | Display the processes in terminal                                             |
| man            | Access manual for all Linux commands                                          |
| grep           | Search for a specific string in an output                                     |
| echo           | Display active processes on the terminal                                      |
| wget           | download files from the internet.                                             |
| whoami         | Create or update passwords for existing users                                 |
| sort           | sort the file content                                                         |
| cal            | View Calendar in terminal                                                     |
| whereis        | View the exact location of any command typed after this command               |
| df             | Check the details of the file system                                          |
| wc             | Check the lines, word count, and characters in a file using different options |

# GIT

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
This is a version control software for developers
Git stores each saved version as a ‘snapshot’ instead of a list of changes made to each file.
You can reference old snapshots whenever you need to and new snapshots are created when your project is modified.
Git also enables you to ‘push’ and ‘pull’ changes to and from installations on other computers.
This makes it what is known as a ‘Distributed Version Control System’, and enables multiple developers to work on the same project.

Version control
---
Version control refers to the process of saving different files or ‘versions’ throughout the various stages of a project
This enables developers to keep track of what has been done and return to a previous phase if they decide they want to revert some of the changes they’ve made.

Branching and Merging
---
Git allows and encourages you to have multiple local branches that can be entirely independent of each other.
The creation, merging, and deletion of those lines of development takes seconds.

## Commands

```bash
git status
git add [file]
git reset [file]
git diff
git diff --staged
git commit -m “[descriptive message]”
git branch
git branch [branch-name]
git checkout
git merge [branch]
git log
git remote add [alias] [url]
git fetch [alias]
git merge [alias]/[branch]
git push [alias] [branch]
git pull
```

## GITHUB

GitHub makes it easier to collaborate using git.
It’s a platform that can hold repositories of code in cloud-based storage so that multiple developers can work on a single project and see each others’ edits in real-time
Plus, it also includes project organisation and management features.
You can assign tasks to individuals or groups, set permissions, and roles for collaborators, and use comment moderation to keep everyone on task.

There are three primary actions you can take when it comes to interacting with other developers’ code on GitHub:

- <u>Fork</u>: The process of copying another’s code from the repository in order to modify it.
-  <u>Pull</u>: When you’ve finished making changes to someone else’s code, you can share them with the original owner via a ‘pull request’.
-  <u>Merge</u>: Owners can add new changes to their projects via a merge, and give credit to the contributors who suggested them.

# Docker

Docker is an open platform for developing, shipping, and running applications.
Docker enables you to separate your applications from your infrastructure so you can deliver software quickly.
With Docker, you can manage your infrastructure in the same ways you manage your applications.
By taking advantage of Docker's methodologies for shipping, testing, and deploying code,
we can significantly reduce the delay between writing code and running it in production

Container
---

A container is an isolated environment for your code.
This means that a container has no knowledge of your operating system, or your files.
It runs on the environment provided to you by Docker Desktop.
Containers have everything that your code needs in order to run, down to a base operating system.

# Cryptography

Cryptography is a technique of securing information and communications through the use of codes
So that only those persons for whom the information is intended can understand and process it.
Thus preventing unauthorized access to information.

Cipher text
---
In cryptography, ciphertext or cyphertext is the result of encryption performed on plaintext using an algorithm, called a cipher.
Ciphertext is also known as encrypted or encoded information because it contains a form of the original plaintext that is unreadable by a human or computer without the proper cipher to decrypt it.
This process prevents the loss of sensitive information via hacking.
Decryption, the inverse of encryption, is the process of turning ciphertext into readable plaintext.
Ciphertext is not to be confused with codetext because the latter is a result of a code, not a cipher

- **Features Of Cryptography**
----
- <b><u>Confidentiality</u></b>
	Information can only be accessed by the person for whom it is intended and no other person except him can access it.
- <b><u>Integrity</u></b>
	Information cannot be modified in storage or transition between sender and intended receiver without any addition to information being detected.
- <b><u>Non-repudiation</u></b>
	The creator/sender of information cannot deny his intention to send information at a later stage.
- <b><u>Authentication</u></b>
	The identities of the sender and receiver are confirmed. As well destination/origin of the information is confirmed.
- <b><u>Interoperability</u></b>
	Cryptography allows for secure communication between different systems and platforms.
- <b><u>Adaptability</u></b>
	Cryptography continuously evolves to stay ahead of security threats and technological advancements.

- **Types Of Cryptography**
----
-  <b><u>Symmetric Key Cryptography</u></b>
	It is an encryption system where the sender and receiver of a message use a single common key to encrypt and decrypt messages.
	Symmetric Key cryptography is faster and simpler but the problem is that the sender and receiver have to somehow exchange keys securely.
	The most popular symmetric key cryptography systems are Data Encryption Systems (DES) and Advanced Encryption Systems (AES).
-  <b><u>Hash Functions</u></b>
	There is no usage of any key in this algorithm.
	A hash value with a fixed length is calculated as per the plain text which makes it impossible for the contents of plain text to be recovered.
	Many operating systems use hash functions to encrypt passwords.
-  <b><u>Asymmetric Key Cryptography</u></b>
	In Asymmetric Key Cryptography, a pair of keys is used to encrypt and decrypt information.
	A receiver’s public key is used for encryption and a receiver’s private key is used for decryption.
	Public keys and Private keys are different.
	Even if the public key is known by everyone the intended receiver can only decode it because he alone knows his private key.
	The most popular asymmetric key cryptography algorithm is the RSA algorithm.
---

![[crypto.png | 500]]