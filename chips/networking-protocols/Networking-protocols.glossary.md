---
title: "Networking-protocols — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [Networking-protocols]
---

- **Acknowledgement (ACK)** — A control message sent by a receiver to indicate successful receipt of a data frame.  
- **Application-layer protocol** — A set of rules defining the format and sequence of messages exchanged between network applications.  
- **Bit stuffing** — A technique to delimit frames by inserting extra bits to prevent confusion with frame boundary markers.  
- **Client-server model** — A network communication model where clients send requests and servers provide responses or services.  
- **Control frame** — A frame type used to carry control information like acknowledgements rather than user data.  
- **Cryptographic checksum (CRC)** — An error detection code used to identify errors in transmitted data frames.  
- **Data frame** — A structured sequence of bits or bytes that carry user data between two directly connected hosts.  
- **Data link layer** — The network layer responsible for framing, error detection, and reliable transmission over a physical link.  
- **Datagram organisation** — A network model where each packet is routed independently and contains full addressing information.  
- **Distance vector routing** — A routing protocol where routers exchange their routing tables periodically to find shortest paths.  
- **Dijkstra’s algorithm** — A graph algorithm used in link-state routing to compute the shortest paths to all network nodes.  
- **Electrical cable** — A physical medium (twisted pair or coaxial) used to transmit electrical signals in networks.  
- **Error detection code** — Additional bits added to data to detect transmission errors.  
- **Ethernet** — A common local area network (LAN) technology that uses port-address tables for forwarding.  
- **Flooding** — A link-state protocol process that reliably distributes link-state packets to all routers in the network.  
- **Forwarding table** — A data structure used in routers to decide the outgoing interface for packets based on destination.  
- **Fragmentation** — Breaking a large packet into smaller packets to cross links with smaller maximum frame sizes.  
- **Go-back-n protocol** — A sliding window reliable protocol retransmitting all unacknowledged frames after a loss.  
- **HELLO message** — Periodic message sent by routers to discover neighbors and detect link failures.  
- **Label switching** — A packet forwarding technique where routers use labels as indices to forwarding table entries.  
- **Link layer** — The layer responsible for the physical transmission and recovery of bits between directly connected devices.  
- **Link state routing** — A routing protocol where routers distribute the entire network topology to compute shortest paths.  
- **Local Area Network (LAN)** — A network connecting multiple devices so they can exchange frames directly.  
- **MAC (Media Access Control) address** — A unique hardware address assigned to network interfaces (implied by context).  
- **Physical layer** — The lowest network layer that transmits raw bits over a physical medium like cables or wireless.  
- **Pipelining** — A technique allowing multiple frames to be sent without waiting for acknowledgements.  
- **Port-address table** — A forwarding data structure used in tree-like networks to map destination addresses to interfaces.  
- **Protocol** — A formal set of rules governing the exchange of messages in network communication.  
- **Reliable protocol** — A data link or transport protocol that ensures correct and ordered delivery of data.  
- **Routing table** — A data structure in routers mapping destinations to next hops and associated metrics.  
- **Selective repeat protocol** — A sliding window protocol retransmitting only individual lost frames, accepting out-of-order frames.  
- **Sequence number** — A number assigned to frames to detect duplicates and losses in reliable transmission protocols.  
- **Sliding window** — A set of sequence numbers representing the allowable frames that can be sent without acknowledgement.  
- **Source routing** — A routing technique where the sender specifies the complete path a packet must follow.  
- **Split horizon** — A distance vector routing technique that prevents routing loops by not advertising routes back to their origin.  
- **Static framing** — Techniques like character or bit stuffing used to define frame boundaries in a bit stream.  
- **Virtual circuit organisation** — A network model where a fixed path is established before data transmission, using labels.  
- **Wireless medium** — A physical medium where data is transmitted via radio or optical signals without wires.
