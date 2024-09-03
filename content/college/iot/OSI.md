# OSI
The Open Systems Interconnection (OSI) model describes seven layers that computer systems use to communicate over a network

7. Application Layer
---
The application layer is used by end-user software such as web browsers and email clients.
It provides protocols that allow software to send and receive information and present meaningful data to users.
application layer protocols are the Hypertext Transfer Protocol (HTTP), File Transfer Protocol (FTP), Post Office Protocol (POP), Simple Mail Transfer Protocol (SMTP), and Domain Name System (DNS).

The Application layer performs the following functions:
• It provides different services such as manipulation of information in several ways, retransferring the files of information, distributing the results etc.
- The functions such as LOGIN or password checking are also performed by the application layer.

6. Presentation Layer
----
The presentation layer prepares data for the application layer.
It defines how two devices should encode, encrypt, and compress data so it is received correctly on the other end.
The presentation layer takes any data transmitted by the application layer and prepares it for transmission over the session layer.
The Presentation layer performs the following functions:
- This layer makes it sure that the information is delivered in such a form that the receiving system will understand and use it.

5. Session Layer
----
The session layer creates communication channels, called sessions, between devices.
It is responsible for opening sessions, ensuring they remain open and functional while data is being transferred, and closing them when communication ends.
The session layer can also set checkpoints during a data transfer—if the session is interrupted, devices can resume data transfer from the last checkpoint.
The Session layer performs the following functions:
- Manages the messages and synchronizes conversations between two different applications.
- It controls logging on and off, user identification, billing and session management.

4. Transport Layer
---
The transport layer takes data transferred in the session layer and breaks it into “segments” on the transmitting end.
It is responsible for reassembling the segments on the receiving end, turning it back into data that can be used by the session layer.
The transport layer  carries out flow control, sending data at a rate that matches the connection speed of the receiving device, and error control, checking if data was received incorrectly and if not, requesting it again.
The Transport layer performs the following functions:
- It decides if the data transmission should take place on parallel paths or single path.
- It performs multiplexing, splitting on the data.
- It breaks the data groups into smaller units so that they are handled more efficiently by the network layer.
The Transport Layer guarantees transmission of data from one end to other end.

3. Network Layer
----
The network layer has two main functions.
One is breaking up segments into network packets, and reassembling the packets on the receiving end.
The other is routing packets by discovering the best path across a physical network.
The network layer uses network addresses (typically Internet Protocol addresses) to route packets to a destination node.
Following are the functions of Network Layer:
- To route the signals through various channels to the other end.
- To act as the network controller by deciding which route data should take.
- To divide the outgoing messages into packets and to assemble incoming packets into messages for higher levels.

2. Data Link Layer
----
The data link layer establishes and terminates a connection between two physically-connected nodes on a network.
It breaks up packets into frames and sends them from source to destination.
This layer is composed of two parts—Logical Link Control (LLC), which identifies network protocols, performs error checking and synchronizes frames, and Media Access Control (MAC) which uses MAC addresses to connect devices and define permissions to transmit and receive data.
The data link layer performs the following functions:
- Performs synchronization and error control for the information which is to be transmitted over the physical link.
- Enables error detection, and adds error detection bits to the data which are to be transmitted.

1. Physical Layer
----
The physical layer is responsible for the physical cable or wireless connection between network nodes.
It defines the connector, the electrical cable or wireless technology connecting the devices, and is responsible for transmission of the raw data, which is simply a series of 0s and 1s, while taking care of bit rate control.
The Physical layer is responsible for the following activities:
- Activating, maintaining and deactivating the physical connection.
- Defining voltages and data rates needed for transmission.
- Converting digital bits into electrical signal.
- Deciding whether the connection is simplex, half duplex or full duplex.

## Advantages of OSI Model
The OSI model helps users and operators of computer networks:
- Determine the required hardware and software to build their network.
- Understand and communicate the process followed by components communicating across a network.
- Perform troubleshooting, by identifying which network layer is causing an issue and focusing efforts on that layer.
The OSI model helps network device manufacturers and
networking software vendors:
 Create devices and software that can communicate with products from any other vendor, allowing open interoperability
 Define which parts of the network their products should work with. Communicate to users at which network layers their product
operates – for example, only at the application layer, or across the stack.
OSI vs. TCP/IP Model
The Transfer Control Protocol/Internet Protocol (TCP/IP) is older
than the OSI model and was created by the US Department of
Defense (DoD). A key difference between the models is that TCP/IP is simpler, collapsing several OSI layers into one:
 OSI layers 5, 6, 7 are combined into one Application Layer in TCP/IP OSI layers 1, 2 are combined into one Network Access Layer in
TCP/IP – however TCP/IP does not take responsibility for
sequencing and acknowledgement functions, leaving these to the
underlying transport layer.
Other important differences:
 TCP/IP is a functional model designed to solve specific
communication problems, and which is based on specific, standard protocols. OSI is a generic, protocol-independent model intended to describe all forms of network communication.
 In TCP/IP, most applications use all the layers, while in OSI simple applications do not use all seven layers. Only layers 1, 2 and 3 are mandatory to enable any data communication.
