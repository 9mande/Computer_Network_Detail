# Computer Network

Understanding a computer network starts with thinking about a connection between two or more computers.  
The main purpose of this connection is sending and receiving data between computer applications.  

## OSI (Open Systems Interconnection) Model

```bash
1. Physical Layer        ┐
2. Data link Layer       ├── Medium Layers
3. Network Layer         ┘
4. Transport Layer       ┐
5. Session Layer         ├── Host Layers
6. Presentation Layer    │
7. Application Layer     ┘
```

Sending data involves a series of steps. OSI Model describes these steps classified into 7 layers.  
It is easy to understand the process of networking with following the OSI Model's 7 layers.  

### Layer 1. Physical Layer

Let's imagine a small local area network(LAN) like below.  
```bash
(PC A)──┬──(PC B)
(PC C)──┘
```
PC A is going to send data to PC B.

The data may move through a physical connection, such as a cable or wireless connection, in the form of an electrical signal.  
At this time, we need our first layer that sends or receives signal and convert signal from analog to digital, digital to analog.  
Furthermore, physical layer may have fixed methods or rules(i.e. protocols) like how to present or distinguish establish and terminate of the signals. In other words, physical layer may define an interface between the device and the medium.  

### Layer 2. Data Link Layer

To send and receive the signals correctly at physical layer, data link layer may have 2 main functions.  

#### MAC (Medium Access Control) Sublayer

First at data link layer, we need a protocol that defines how to use the shared medium (a cable). Also, we need an physical address for each device connected in the network, so that the data can arrive to a correct device in the network (now, PC B not PC C). That's the MAC address.

#### LLC (Logical Link Control) Sublayer

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

Now data has arrived at the right host. But the host may have some applications that uses network. To direct data to a specific application, an unique number is needed. This number is known as the port number. And each application's network end point (i.e. socket) is binded to the IP address and the port. Then, we can find an application using port number.

#### Connection-Oriented, Connectionless

There are two famous protocol of the transport layer, TCP(Transmission Control Protocol) and UDP(User Datagram Protocol).  
TCP is a connection-oriented protocol which means the data transfer only occurs during a connection. It has more processes to establish the connection, to end the connection. And also checks if the data passed correctly.
UDP is a connectionless protocol which means the data transfer can occur any time.  

Connection-oriented protocols ensure reliable data transmission. But the server has to establish a socket for each connected client. As the number of clients increases, the server load increases.  
Connectionless protocols can use just one socket for all connected clients. But it does not guarantees a reliable data transmission.

### Layer 5. Session Layer

From layer 1 to 4, the lower layers, the main function was about delivering data.  
From layer 5 to 7, the upper layers, the main function is about communicating between applications of different PCs.  

Especially when a connection needs to be persisted, we call this connection a session. If not, session is not defined.  
Session could be set up, be maintained, and released.  
Protocols for how to communicate, synchronize are also included in this layer.  
Session is usually used at client-server model. If client requests resources to server, server responses.  

#### Stateful, Stateless

There's another feature to think which is about state.
If a server stores informations about the session, it is called a stateful server.  
If a server doesn't store informations about the session, it is called a stateless server.

A stateful server stores the session information with clients. The server can respond quickly based on the session state.  
A stateless server does not save any session informations. The server responses regardless of the session state. So, a client has to send all informations to the server when requests.	And this makes longer message.  

Stateful code has side effects, which means it has some effects other than its primary effect after the operation.
Stateless structure has ease of scaling.

### Layer 6. Presentation Layer

Before and after delivering data, there are several reprocessing of data.  

One of that is data formatting.  
This is needed because application layer treats variety of data types such as image.  
At sender's side, the presentation layer converts the data from sender's supported format into a generic format.  
At receiver's side, the presentation layer converts the generic format into a receiver's supported format.  
So, only the generic format is used while transfer.  

Second is encryption and decryption of data which is used for carrying sensitive information.

Last one is compression, reducing the size of data.

### Layer 7. Application Layer

The application layer is the top layer of OSI 7 layers which can only directly communicate with human.  
This layer acts like an interface for applications to use network services.  
For example, SMTP (Simple Mail Transfer Protocol) provides a library for each programming language so that application can be made involving mailing function.

## References

- [CS-310 Lecture 03 - Stateless Services / Youtube / Steve Tarzia](https://www.youtube.com/watch?v=XnFsxRDnthg)
- [Networking Lecture 02 - The Internet Core and Layering / Youtube / Steve Tarzia](https://www.youtube.com/watch?v=dZx8WdQI3Hw)
- [The importance of being stateless](https://cerfacs.fr/coop/stateful-stateless)