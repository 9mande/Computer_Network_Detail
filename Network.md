# Computer Network

Understanding a computer network starts with thinking about a connection between two or more computers.  
The main purpose of this connection is sending data between computer applications.  

## OSI (Open Systems Interconnection) Model

Sending data involves a series of steps. OSI Model describes these steps classified into 7 layers.  
It is easy to understand the process of networking with following the OSI Model's 7 layers.  

Let's imagine a small local area network(LAN) like below.  
```bash
(PC A)──┬──(PC B)
(PC C)──┘
```
PC A is going to send data to PC B.

### Layer 1. Physical Layer

The data may move through a physical connection, such as a cable or wireless connection, in the form of an electrical signal.  
At this time, we need our first layer that sends or receives this signal and convert signals from analog to digital, digital to analog.  
Furthermore, physical layer may have fixed methods or rules about how to present or distinguish establish and terminate of the signals.  
(In computer network, protocol means these fixed methods or rules.)  

### Layer 2. Data Link Layer

To send and receive the signals correctly at physical layer, data link layer may have 2 main functions.  

First at data link layer, we need a protocol that defines how to use the shared medium (a cable). Also, we need an address for each device connected in same network so that the data can arrive to a correct device in the network (now, PC B not PC C).  
Second, data link layer is responsible for ensuring that data is passed correctly. If there's an error detected from the data, it can retransmit. Also, it can contain functions to control flow of transmission.  

### Layer 3. Network Layer

Let's enlarge the situation little bit like below.  
```bash
(PC A)──┬──(PC B)  ││  (PC D)──┬──(PC E)
(PC C)──┴───────(Router)───────┴──(PC F)
```
Now, if PC A wants to send data to PC D, PC A cannot just use address from layer 2 since PC D is in another LAN. (Maybe not impossible for this example, but for big network like Internet, it gets really hard to.)  
So, at the network layer, there's an individual logical, hierarchical address called IP assigned to each PC. It's called a host when a network node assigned a network address. With this address, the data can be transfered to any other PCs of any other LANs.  
In other words, the network layer contains routing process which allows Internetworking.  

### Layer 4. Transport Layer

Network layer was a layer that helps logical connection between hosts with logical address.  
Transport layer is, a layer that helps logical connection between applications of each host.

A host may have several applications that uses network. To direct data to a specific application, a unique number is needed. This number is known as the port number. And each application's network end point (i.e. socket) is binded to the IP address and the port.  

### Layer 5. Session Layer

From layer 1 to 4, the lower layers, the main function was about delivering data.  
From layer 5 to 7, the upper layers, the main function is about communicating between applications.  

Session layer provides applications with several ways to manage the connection.  
Especially when a connection needs to be persisted, we call this connection a session. If not, the session is not defined.  
The session could be set up, be maintained, and released.  
Maintaining session means making sure that things are not getting dropped. If a session drops, it's going to re-establish that session.

### Layer 6. Presentation Layer

Before and after delivering data, there are several reprocessing of data.  

One of that is data formatting.   
At sender's side, the presentation layer converts the data from sender's supported format into a generic format.  
At receiver's side, the presentation layer converts the generic format into a receiver's supported format.  

Second is encryption and decryption of data which is used for carrying sensitive information.

Last one is compression, reducing the size of data.

### Layer 7. Application Layer

The application layer acts like an interface for user applications to use network services.
