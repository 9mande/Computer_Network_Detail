# Computer Network
Understanding a computer network starts with thinking about a connection between two or more computers.  
The main purpose of this connection is sending a data from one computer, to another computer.  

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

## Layer 2. Data Link Layer

To send and receive the signals correctly at physical layer, data link layer may have 2 main functions.  

First at this layer, we need a protocol that defines how to use the shared medium (now, a cable). Also, we need an address for each device connected in same network so that the data can arrive to a correct device in the network (now, PC B not PC C).  
Second, this layer is responsible for ensuring that data is passed correctly. If there's an error detected from the data, it can retransmit. Also, it can control flow of transmission.  

## Layer 3. Network Layer

Let's enlarge the situation little bit like below.  
```bash
(PC A)──┬──(PC B)  ││  (PC D)──┬──(PC E)
(PC C)──┴───────(Router)───────┴──(PC F)
```
Now, if PC A wants to send data to PC D, PC A cannot just use address from layer 2 since PC D is in another LAN. (Maybe not impossible for this example, but for big network like Internet, it gets really hard to.)  
So, at network layer, there's a individual logical, hierarchical address. With this address, the data can be transfered to any other PCs of any other LANs.  

## Layer 4. Transport Layer

## Layer 5. Session Layer

## Layer 6. Presentation Layer

## Layer 7. Application Layer


## Breif Elements
To be a little bit more specific, we have to consider some elements below.
- Sender Software (Application or Service, like Email Service)
- Sender PC
- Physical connection between PCs (like a cable)
- Receiver PC
- Receiver Software
