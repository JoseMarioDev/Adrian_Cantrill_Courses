## 🗒️ Notes

👨🏽‍💻 YAML 101

- collection of key/value pairs
- supports strings, floats, ints, bool, lists, dict
- supports lists

  - lists can be inline
  - or indented with dashes "-"

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6ce47b18-cefd-4771-a5b0-d0d18655f81b/Screen_Shot_2021-05-10_at_3.28.33_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6ce47b18-cefd-4771-a5b0-d0d18655f81b/Screen_Shot_2021-05-10_at_3.28.33_PM.png)

- values can be in parentheses or not, both are valid
- supports dictionaries - a list of dictionaries
- is used for [CloudFormation](https://www.notion.so/CloudFormation-b92ad6a9f91d4cbf9d879fea5f1fb61d)
- indentation matters

---

👨🏽‍💻 JSON 101

- key/value pairs
- similar to YAML but format is just different
- doesn't care about indentation
- values can be string, obj, num, array, bool, or null
- supports objects and arrays. can be nested
- used for AWS policies

---

🔑 Encryption 101 - part 1

encryption approaches

- encryption at rest - data stored in hardware in encrypted form
- encryption in transit - apply encryption wrapper while data is being transferred

concepts

- Plaintext - unencrypted data
- Algorithm - code takes plaintext and key and encrypts data
- key - password
- Ciphertext - result of data that is encrypted with algorithm and key

symmetric encryption

- same key is used for encryption and decryption process
- good for local encryption like data on a laptop
- not so good when data needs to be sent over network between parties

asymmetric encryption

- uses 2 keys - public key and private key
- no requirement to exchange keys in advance
- used when 2 or more parties are involved and havent met before
- used by SSL, TLS, PGP, SSH
- much more difficult to do vs symmetric

---

🔑 Encryption 101 - part 2

signing

- when receiver acknowledges to sender message received
- receiver sends message encrypted w/private key to sender
- sender uses public key to decrypt message and verify if private key is correct
- inverse of asymmetric encryption process
- used for ID verification and login systems

steganography

- process of hiding something in something else
- think of "using invisible ink" in spy tactics
- embed data in other data

---

🌎 Network Starter Pack - OSI Model

OSI Model

higher layers build on lower layers

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fd7c330e-3b14-48d7-831f-87269dd7b703/Screen_Shot_2021-05-10_at_4.54.08_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fd7c330e-3b14-48d7-831f-87269dd7b703/Screen_Shot_2021-05-10_at_4.54.08_PM.png)

---

🌎 Network Starter Pack Layer 1 - Physical

- physical medium can be copper, fiber, or wifi
- used to connect computers together
- hardware: hub - repeats to all devices on network, including collisions
- no access control
- no unique identified devices

---

🌎 Network Starter Pack Layer 2 - Data Link

- uses Frames - format for sending data over network
- hardware: switch
  - store and forward frames
  - keeps mac address table. learns which devices are connected
  - doesn't forward collisions
- mac addresses - unique hardware address for each NIC
- frame is a container w/components

  - preamble
  - destination/source mac addresses
  - ethertype - specify layer 3 protocol
  - payload - data frame is sending
  - frame check sequence

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/be619681-5196-4342-8cf2-1988e2463636/Screen_Shot_2021-05-13_at_8.18.38_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/be619681-5196-4342-8cf2-1988e2463636/Screen_Shot_2021-05-13_at_8.18.38_AM.png)

- CSMA/CD
  - carrier sense multiple access/collision detection
  - sender listens to see if traffic is on layer 1. if not, it sends frame to receiver
  - if it senses traffic, it's backs away for a random time and tries again
  - uses encapsulation(taking data wrapping it in something else), layer 3 loads payload inside frame to send

---

🔢 Decimal to Binary Conversion - IP Addressing

- how to convert from dec to bin
- focuses on IPv4
- 32 bits, 4 x 8bits
- 8 bits in a byte

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2c97180b-93e7-4dc8-b1d6-5681042368a7/Screen_Shot_2021-05-13_at_8.37.40_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2c97180b-93e7-4dc8-b1d6-5681042368a7/Screen_Shot_2021-05-13_at_8.37.40_AM.png)

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/79628a91-335c-4ab6-83e3-0e2cea5da02a/Screen_Shot_2021-05-13_at_8.40.25_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/79628a91-335c-4ab6-83e3-0e2cea5da02a/Screen_Shot_2021-05-13_at_8.40.25_AM.png)

---

🌎 Network Starter Pack Layer 3 - Network

Fundamentals

- adds ability for cross-network addressing(IP addresses)
- uses Packets to route across different layer 2 networks via Layer 2 encapsulation
- hardware: router
- forwards decisions using route and route tables
- every IPv4 packet has:
  - source/destination IP address
  - protocol field - Layer 4(TCP, UDP, ICMP)
  - Data - generated from Layer 4 protocol
  - TTL
- every IPv6 packet has:
  - source/dest IP address
  - data
  - hop limit - similar to TTL

IP addressing v4

- dotted decimal notation - ex: 133.33.3.7
- 2 parts
  - network part and host part
  - if network part of 2 ip addresses match, they are on the same network
  - if not, they are on diff networks
- assigned either statically or dynamically
- want them to be unique

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dae03330-697c-4661-acce-f3ffa729b538/Screen_Shot_2021-05-13_at_9.21.48_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dae03330-697c-4661-acce-f3ffa729b538/Screen_Shot_2021-05-13_at_9.21.48_AM.png)

Subnet Mask

- allow host to determine if IP addresses it needs to communicate with is local or remote
- determines if needs use gateway or can communicate locally

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/db226f40-08c0-47f8-93ea-0200b81c92f3/Screen_Shot_2021-05-13_at_9.28.18_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/db226f40-08c0-47f8-93ea-0200b81c92f3/Screen_Shot_2021-05-13_at_9.28.18_AM.png)

Route Tables & Routes

- every router as at least 1 table attached to a NIC
- table is a collection of routes with destination and next hop
- /32 means 1 specific IP addresses. /0 means all IPs

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69e814dc-fcc9-4193-8d21-f33c76ded276/Screen_Shot_2021-05-13_at_9.43.39_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69e814dc-fcc9-4193-8d21-f33c76ded276/Screen_Shot_2021-05-13_at_9.43.39_AM.png)

ARP - Address Resolution Protocol

- used for layer 3 packet to encapsulate inside a frame
- find mac address for an ip address

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3f01027a-8a34-401c-a485-f07ff8847d79/Screen_Shot_2021-05-13_at_9.48.57_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3f01027a-8a34-401c-a485-f07ff8847d79/Screen_Shot_2021-05-13_at_9.48.57_AM.png)

Routing example

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/491a6710-64ab-4aa3-ac29-0751ccb59eb1/Screen_Shot_2021-05-13_at_9.54.24_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/491a6710-64ab-4aa3-ac29-0751ccb59eb1/Screen_Shot_2021-05-13_at_9.54.24_AM.png)

Summary

- Layer 3 adds IP addresses, ARP, Routes, Route Tables, Routers
- device to device communication over internet
- no method for channels of communication - Layer 4
- can be delivered out of order

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/54b61b77-222e-4dca-81f4-16eed1ef2e06/Screen_Shot_2021-05-13_at_9.57.56_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/54b61b77-222e-4dca-81f4-16eed1ef2e06/Screen_Shot_2021-05-13_at_9.57.56_AM.png)

---

🌎 Network Starter Pack Layers 4 and 5 - Transport and Session

Concepts

- Transport layer runs on top of network layer. Session runs on top of Transport
- limitations of layer 3
  - packets are routed independently, might arrive to receiver out or order
  - provides no method of assuring method arrival
  - packets can go missing
  - no method of splitting by app or channel
  - ip has no flow control. if sender is sending packets too fast for receiver

TCP/UDP

- TCP
  - reliable
  - error correction
  - ordering of data
  - HTTP/HTTPS/SSH
  - establishes handshake
- UDP
  - less reliable
  - faster
  - doesnt error correct nor handshake
- TCP Segments
  - encapsulated in IP packets
  - dont have src or dst IPs. provided by packets
  - Do have src/dst ports
  - has sequence number to correctly order segments at receiver
  - acknowledgement field
  - flags
  - window - flow control, indicates how much can receive
  - checksum
  - urgent pointer
  - data

TCP Architecture

- how connections works
- creates 2 streams using well known ports and ephemeral ports

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0fdcdf1f-f400-456f-a995-758ef0f4f1ae/Screen_Shot_2021-05-14_at_12.33.45_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0fdcdf1f-f400-456f-a995-758ef0f4f1ae/Screen_Shot_2021-05-14_at_12.33.45_PM.png)

- 3 way handshake flags
- SYN sends sequence number
- SYN-ACK sequence num + Acknowledge
- ACK sender acknowledges receipt of acknowledgement

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7f9bfda8-4f8b-46c7-ac47-15cfdee02f59/Screen_Shot_2021-05-14_at_12.46.43_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7f9bfda8-4f8b-46c7-ac47-15cfdee02f59/Screen_Shot_2021-05-14_at_12.46.43_PM.png)

Sessions & State

- stateless firewalls see two things
- two rules will be required out and in - AWS NaCL
- Stateful firewalls sees one things automatically allows out and in - AWS Security Groups

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/539d61af-5964-45d0-b6e0-8b86521cd331/Screen_Shot_2021-05-14_at_12.49.48_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/539d61af-5964-45d0-b6e0-8b86521cd331/Screen_Shot_2021-05-14_at_12.49.48_PM.png)

Well Known Ports

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fb38226d-e515-420c-99f2-a6f499a31541/Screen_Shot_2021-05-14_at_12.50.51_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fb38226d-e515-420c-99f2-a6f499a31541/Screen_Shot_2021-05-14_at_12.50.51_PM.png)

---

🌎 Network Starter Pack - NAT

Concepts

- process of adjusting packet's src/dest addresses to allow transit between diff networks
- overcome shortage of IPv4 addresses
- provides security benefits

Static NAT

- 1 private to 1 fixed public address - IGW

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4a1f8190-f016-469a-826a-96a8860a5b59/Screen_Shot_2021-05-14_at_3.17.58_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4a1f8190-f016-469a-826a-96a8860a5b59/Screen_Shot_2021-05-14_at_3.17.58_PM.png)

Dynamic NAT

- 1 private to 1st available public IP
- given IP from a pool
- temporary

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7d48931b-f9e2-4702-86cf-2ebb43fbf0b8/Screen_Shot_2021-05-14_at_3.21.21_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7d48931b-f9e2-4702-86cf-2ebb43fbf0b8/Screen_Shot_2021-05-14_at_3.21.21_PM.png)

Port Address Translation(PAT)

- many private to 1 public - NATGW

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c8731906-fc88-4eb8-bad6-a104e289f025/Screen_Shot_2021-05-14_at_3.25.51_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c8731906-fc88-4eb8-bad6-a104e289f025/Screen_Shot_2021-05-14_at_3.25.51_PM.png)

---

🌎 Network Starter Pack - Subnetting

Concepts

- IP classes were broken into classes - A, B, C

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/302ce9f9-5e69-49f5-866e-6f4617635e33/Screen_Shot_2021-05-15_at_9.22.48_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/302ce9f9-5e69-49f5-866e-6f4617635e33/Screen_Shot_2021-05-15_at_9.22.48_AM.png)

Private Range of IPs

- were setup to be used for internal networks. not public for internet. 1 range for each class - A, B, C
- use NAT to access internet because IP addresses were running out
- IPv6 was created to solve problem, so many addresses available it won't run out

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/06c8528a-0372-4257-bc21-87235b42e171/Screen_Shot_2021-05-15_at_9.25.18_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/06c8528a-0372-4257-bc21-87235b42e171/Screen_Shot_2021-05-15_at_9.25.18_AM.png)

Subnetting

- process of breaking down IP range into pieces
- done by diving larger network/2, then breaking down those parts further if need be
- CIDR uses /num

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/14333452-8ab7-4618-bb71-fd707ef8dd2b/Screen_Shot_2021-05-15_at_9.35.43_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/14333452-8ab7-4618-bb71-fd707ef8dd2b/Screen_Shot_2021-05-15_at_9.35.43_AM.png)

Subnetting example

- breaking down a /16 network

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e58422b3-839d-42b8-a154-5c207be9f3c1/Screen_Shot_2021-05-15_at_9.43.00_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e58422b3-839d-42b8-a154-5c207be9f3c1/Screen_Shot_2021-05-15_at_9.43.00_AM.png)

---

🚫 Distributed Denial of Service Attack

Concepts

- attacks designed to overload websites
- competes against legitimate connections
- distributed. hard to block individual IPs/ranges
- three categories of attacks

  - application layer - http flood

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2391ac69-4fd0-4d84-a451-74d2fcd583b8/Screen_Shot_2021-05-15_at_1.07.20_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2391ac69-4fd0-4d84-a451-74d2fcd583b8/Screen_Shot_2021-05-15_at_1.07.20_PM.png)

  - protocol attack - SYN flood

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4eb9f525-c866-4b75-90c2-51c07cf806bf/Screen_Shot_2021-05-15_at_1.08.55_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4eb9f525-c866-4b75-90c2-51c07cf806bf/Screen_Shot_2021-05-15_at_1.08.55_PM.png)

  - volumetric attacks - DNS Amplification

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8cb8f852-dc39-47f7-86db-3009bdae0d3e/Screen_Shot_2021-05-15_at_1.10.30_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8cb8f852-dc39-47f7-86db-3009bdae0d3e/Screen_Shot_2021-05-15_at_1.10.30_PM.png)

  - involves bots usually

---

🛣️. SSL and TLS

Concepts

- TLS is newer, more secure version os SSL
- provides privacy and data integrity between client/server
- makes sure communications are encrypted
- uses asymmetric at first, then moves to symmetric for ongoing(easier to perform)
- identity verification - server or client/server verified
- reliable connection - protect again alteration of data in transit

Three phases to secure communication

- operates at Layer 4
  1. Cipher Suites - set of protocols used by TLS
     - algorithms grouped together
     - client/server must agree on what cipher suite to use
  2. Authentication
     - client verifies server id by verifying it's SSL cert with PCA
     - PCA = public certificate authority
     - client encrypts data and sends to server to verify server has private key
  3. Key exchange
     - move to symmetric encryption
     - generates premaster key and it's used to create a master secret which is used going forward

Visual architecture

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/456160ac-5b4f-4a50-bdf1-047ba17f1a9e/Screen_Shot_2021-05-15_at_1.26.28_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/456160ac-5b4f-4a50-bdf1-047ba17f1a9e/Screen_Shot_2021-05-15_at_1.26.28_PM.png)
