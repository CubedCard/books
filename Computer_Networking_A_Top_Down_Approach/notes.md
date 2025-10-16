# Notes (Computer Networking: A Top-Down Approach — Kurose & Ross)

> Summarized from personal study notes, 2017 edition.  
> These notes follow the book’s top-down organization — from applications to physical transmission — and include core concepts, key protocols, and security mechanisms.

---

## 📘 Table of Contents
- [Chapter 1 — Computer Networks and the Internet](#chapter-1--computer-networks-and-the-internet)
  - [Messages and Packets](#11-messages-and-packets)
  - [Network Structure](#12-network-structure)
  - [Delays, Loss, and Throughput](#13-delays-loss-and-throughput)
  - [Protocol Layering](#14-protocol-layering)
  - [Security](#15-security)
- [Chapter 2 — Application Layer](#chapter-2--application-layer)
  - [Architectures](#21-architectures)
  - [Processes and Sockets](#22-processes-and-sockets)
  - [HTTP](#http)
  - [Email](#23-email)
  - [DNS](#24-dns)
  - [P2P File Sharing](#25-p2p-file-sharing)
- [Chapter 3 — Transport Layer](#chapter-3--transport-layer)
  - [Overview](#31-overview)
  - [Multiplexing and Demultiplexing](#32-multiplexing-and-demultiplexing)
  - [UDP](#33-udp)
  - [TCP](#34-tcp)
- [Chapter 4 — Network Layer](#chapter-4--network-layer)
  - [Overview](#41-overview)
  - [Inside a Router](#42-inside-a-router)
  - [IP and Addressing](#43-ip-and-addressing)
- [Chapter 5 — Link Layer and LANs](#chapter-5--link-layer-and-lans)
  - [Overview](#51-overview)
  - [Error Detection and Correction](#52-error-detection-and-correction)
- [Chapter 6 — Network Security](#chapter-6--network-security)
  - [Goals](#61-goals)
  - [Cryptography](#62-cryptography)
  - [Integrity and Authentication](#63-integrity-and-authentication)
  - [Secure Communication Protocols](#64-secure-communication-protocols)
  - [Network-Layer Security: IPsec and VPNs](#65-network-layer-security-ipsec-and-vpns)
  - [Firewalls and Intrusion Detection](#66-firewalls-and-intrusion-detection)
- [Appendix — OSI Model](#appendix--osi-model)

---

## Chapter 1 — Computer Networks and the Internet

### 1.1 Messages and Packets
Network applications exchange **messages** containing arbitrary data.  
Messages are divided into **packets** that travel through **communication links** and **packet switches** (routers or switches).  
Each link transmits at its full rate.

**Store-and-forward transmission:**  
Routers must receive the entire packet before forwarding — doubling transmission time.

**Queuing delay and packet loss:**  
Packets wait in **output buffers**; full buffers cause **packet loss**.

**Forwarding and routing:**  
Routers use **forwarding tables**, filled by **routing protocols**, to decide the next hop.

---

### 1.2 Network Structure
Internet hierarchy:
1. **Access ISPs** (home, business connections)
2. **Regional ISPs**
3. **Tier-1 ISPs** (global backbones)

**PoPs (Points of Presence):** connection points where smaller ISPs plug into larger ones.  
**Peering and IXPs:** ISPs can directly exchange traffic without paying (settlement-free).

**Content-provider networks:**  
Companies like Google operate their own global networks, connecting directly to lower-tier ISPs to cut costs and latency.

---

### 1.3 Delays, Loss, and Throughput
**Total nodal delay =** processing + queuing + transmission + propagation.

- *Processing delay:* check headers/errors (μs)
- *Queuing delay:* waiting in buffer (μs–ms)
- *Transmission delay:* `L/R` — time to send bits
- *Propagation delay:* `d/s` — time to travel link

**Throughput:** limited by the slowest link — the **bottleneck**.  
When offered load > capacity (`La/R > 1`), queues fill and packets are dropped.

---

### 1.4 Protocol Layering
A **layered architecture** brings modularity.

| Layer | Example Protocols | Data Unit |
|-------|-------------------|------------|
| Application | HTTP, SMTP, FTP, DNS | Message |
| Transport | TCP, UDP | Segment |
| Network | IP | Datagram |
| Link | Ethernet, Wi-Fi | Frame |
| Physical | Copper, fiber | Bit |

**Encapsulation:** each layer adds its own header to the data from above.

---

### 1.5 Security
- **Malware:** viruses (need execution) and worms (self-replicating)  
- **DDoS:** bandwidth or connection flooding  
- **Packet sniffers:** capture traffic  
- **IP spoofing:** falsify sender address  

---

## Chapter 2 — Application Layer

### 2.1 Architectures
Two main types:
- **Client–Server:** centralized, always-on host with fixed IP.  
- **Peer-to-Peer (P2P):** distributed, scalable, low cost, but less secure.

---

### 2.2 Processes and Sockets
A **process** is a running program.  
Remote processes communicate via **sockets**, identified by:
- IP address (host)
- Port number (process)

Example ports: HTTP (80), SMTP (25).  
Client initiates; server waits.

---

### HTTP
**Stateless protocol.**  
Two modes:
- **Non-persistent:** one request per TCP connection (2 RTTs)
- **Persistent:** multiple requests per connection

**Messages:**
- *Request:* line + headers + optional body  
- *Response:* status line + headers + body  

**Cookies:** maintain client state.  
**Proxies/Caches:** store popular content locally; **conditional GETs** ensure freshness.

---

### 2.3 Email
**Components:** user agents, mail servers, SMTP protocol (TCP port 25).  
**Retrieval:** via POP3, IMAP, or HTTP webmail.

- SMTP → push-based  
- HTTP → pull-based

---

### 2.4 DNS
Resolves hostnames to IP addresses (UDP port 53).

**Hierarchy:**
Root → TLD → Authoritative servers  
**Records:**  
- A (address),  
- NS (name server),  
- CNAME (alias),  
- MX (mail).

**Caching:** improves efficiency, short TTL keeps records fresh.

---

### 2.5 P2P File Sharing
**BitTorrent:**  
- Files split into 256 KB chunks.  
- Peers exchange chunks; “rarest first” ensures good distribution.  
- A **tracker** coordinates peers.  
- Peers prefer those who upload fastest (“top 4” reciprocation).

---

## Chapter 3 — Transport Layer

### 3.1 Overview
Provides **logical communication** between processes.  
Encapsulates messages → **segments** → **datagrams** → **frames**.

| Protocol | Connection | Reliability | Use Cases |
|-----------|-------------|--------------|------------|
| UDP | No | Best effort | DNS, VoIP, streaming |
| TCP | Yes | Reliable, ordered | Web, email, file transfer |

---

### 3.2 Multiplexing and Demultiplexing
- **UDP socket:** (dest IP, dest port)  
- **TCP socket:** (src IP, src port, dest IP, dest port)  
Ports 0–1023 are reserved (HTTP 80, FTP 21, DNS 53).

---

### 3.3 UDP
Simple and connectionless.  
Adds:
- Ports for addressing  
- Checksum for error detection  
No flow or congestion control.

---

### 3.4 TCP
**Full-duplex, point-to-point**.  
**Header:** ports, sequence #, acknowledgment #, window size, flags (SYN, ACK, FIN).

**Reliable data transfer:**  
Cumulative ACKs confirm receipt of bytes.  
Lost segments are retransmitted.

**Connection lifecycle:**
- **Handshake:** SYN → SYNACK → ACK  
- **Teardown:** FIN → ACK → FIN → ACK  
**States:** CLOSED → ESTABLISHED → TIME_WAIT.

---

## Chapter 4 — Network Layer

### 4.1 Overview
Two planes:
- **Data plane:** per-packet forwarding (hardware, fast)  
- **Control plane:** routing (software, slower)

**SDN (Software Defined Networking):** central controller programs routers remotely.

---

### 4.2 Inside a Router
Main components:
- **Input ports** → receive & lookup  
- **Switching fabric** → connects inputs to outputs  
- **Output ports** → queue & transmit  
- **Routing processor** → manages routing logic

**Switching methods:** memory, bus, interconnection network.

---

### 4.3 IP and Addressing
**IPv4 header:** version, TTL, protocol, checksum, addresses.  
**MTU:** max frame size; large packets get **fragmented**.

**Addressing:**  
CIDR (e.g. `192.168.1.0/24`) defines subnets.  
**DHCP:** dynamically assigns IPs (discover → offer → request → ACK).  
**NAT:** maps private addresses to one public address.

**IPv6:**  
128-bit addresses, 40-byte fixed header, no fragmentation, no checksum.  
Transition via **tunneling**.

**ICMP:**  
For diagnostics (ping, traceroute).

---

## Chapter 5 — Link Layer and LANs

### 5.1 Overview
**Node:** device running link-layer protocol.  
**Link:** channel between adjacent nodes.  
Packets from network layer are encapsulated into **frames**.

**Services:**
- Framing  
- MAC (Medium Access Control)  
- Optional reliable delivery  
- Error detection/correction

**Network adapter (NIC):** hardware implementing link-layer logic.

---

### 5.2 Error Detection and Correction
- **Parity bits:** detect single-bit errors.  
- **Checksums:** low-cost, weak detection.  
- **CRC (Cyclic Redundancy Check):** robust, hardware-friendly.  
- **FEC (Forward Error Correction):** receiver can both detect and correct.

---

## Chapter 6 — Network Security

### 6.1 Goals
1. **Confidentiality:** only sender/receiver can read (encryption)  
2. **Integrity:** detect modifications  
3. **Authentication:** verify identities  
4. **Operational security:** firewalls, IDS/IPS

---

### 6.2 Cryptography
- **Symmetric:** one shared secret key  
- **Public-key:** private/public pair  
- **Historical ciphers:** Caesar, monoalphabetic, polyalphabetic  
**Attack models:** ciphertext-only, known-plaintext, chosen-plaintext.

---

### 6.3 Integrity and Authentication
- **Hash functions:** e.g., SHA produce fixed-size digests.  
- **MAC (Message Authentication Code):** hash + secret key.  
- **Digital signatures:** encrypt hash with private key → verifiable by anyone using the public key.  
- **Certificates & CAs:** bind public keys to verified identities.

---

### 6.4 Secure Communication Protocols
**SSL/TLS (used in HTTPS):**
Adds confidentiality, integrity, and authentication on top of TCP.

**Handshake steps:**
1. Exchange supported algorithms + nonces  
2. Server sends certificate  
3. Client verifies, sends encrypted pre-master secret  
4. Both derive session keys (2 encryption + 2 MAC)  
5–6. Exchange MACs to confirm success  

**Nonces:** prevent replay of sessions.  
**Sequence numbers:** prevent reordering.

---

### 6.5 Network-Layer Security: IPsec and VPNs
**IPsec:** secures IP datagrams end-to-end.  
- **AH:** authentication + integrity  
- **ESP:** authentication + integrity + confidentiality  
Used in **VPNs** to safely tunnel over public Internet.

---

### 6.6 Firewalls and Intrusion Detection
**Firewalls:**
- *Packet filters:* stateless, rule-based  
- *Stateful filters:* track TCP connection states  
- *Application gateways:* app-specific proxies  

**IDS/IPS:**
- *Signature-based:* detect known attacks  
- *Anomaly-based:* detect unusual behavior  
**Snort:** open-source IDS with community signature database.

---

## Appendix — OSI Model
The **OSI model** has seven layers:

1. Physical  
2. Data Link  
3. Network  
4. Transport  
5. Session  
6. Presentation  
7. Application  

The Internet architecture merges session & presentation into the application layer.

---


