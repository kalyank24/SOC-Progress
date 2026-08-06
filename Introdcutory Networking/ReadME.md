
<h1>Introductry Networking</h1>


<img src="https://github.com/kalyank24/SOC-Progress/blob/main/Introdcutory%20Networking/images/Introductry.png" alt="Introductry Networking">

<p># Computer Networking Basics

## Overview

In this room, we learned the basic principles of computer networking.

Networking is a vast topic, but understanding the fundamentals and key concepts is sufficient for building a strong foundation as a SOC Analyst.

## Topics Covered

1. Brief overview of the OSI Model
2. TCP/IP Model
3. How these models work in practice
4. Introduction to basic networking tools

---

# OSI Model

The **OSI (Open Systems Interconnection) Model** is a standardized reference model used to explain how data is transmitted across a network. It consists of **seven layers**, each with a specific responsibility.

## The Seven Layers

1. Application Layer
2. Presentation Layer
3. Session Layer
4. Transport Layer
5. Network Layer
6. Data Link Layer
7. Physical Layer

<img src= "https://github.com/kalyank24/SOC-Progress/blob/main/Introdcutory%20Networking/images/OSI.png" alt = "OSI">
---

## 1. Application Layer

The **Application Layer** provides network services directly to end-user applications. It acts as the interface between users and network services, allowing applications to communicate over the network using protocols such as **HTTP, HTTPS, FTP, SMTP, SSH, and RDP**.

Once the application generates data, it is passed down to the **Presentation Layer** for further processing.

---

## 2. Presentation Layer

The **Presentation Layer** receives data from the Application Layer and converts it into a standardized format that both the sender and receiver can understand.

Its primary responsibilities include:

* Data translation
* Data encryption and decryption
* Data compression
* Data formatting

These processes ensure that data can be transmitted efficiently and securely between systems.

---

## 3. Session Layer

The **Session Layer** establishes, manages, and terminates communication sessions between two devices.

Its responsibilities include:

* Establishing a session between the sender and receiver
* Maintaining synchronization throughout the communication
* Managing the session until the communication is complete

Once the session is established, the data is passed to the **Transport Layer**.

---

## 4. Transport Layer

The **Transport Layer** is responsible for ensuring reliable or fast data transmission between devices. It determines which transport protocol should be used.

The two most common protocols are:

### TCP (Transmission Control Protocol)

TCP is a **connection-oriented protocol**. Before transmitting data, it establishes a connection between the sender and receiver using the **Three-Way Handshake**. This ensures reliable and ordered delivery of data.

Data transmitted over TCP is called **segments**.

### UDP (User Datagram Protocol)

UDP is a **connectionless protocol**, often referred to as a **"fire-and-forget"** protocol. It sends data without establishing a connection and does not verify whether the data has been received successfully.

Data transmitted over UDP is called **datagrams**.

---

## 5. Network Layer

The **Network Layer** is responsible for determining the best path for data to reach its destination.

It uses **logical addressing (IP addresses)** to identify and communicate with devices across different networks.

For example, when accessing a website, the destination server is identified using its IP address.

---

## 6. Data Link Layer

The **Data Link Layer** is responsible for communication between devices on the same local network.

Its functions include:

* Physical addressing using **MAC addresses**
* Error detection
* Error correction
* Framing data for transmission

Every network-enabled device contains a **Network Interface Card (NIC)** with a unique **MAC address**, which is used for communication within the local network.

---

## 7. Physical Layer

The **Physical Layer** represents the hardware used for network communication.

It is responsible for transmitting raw binary data as electrical, radio, or optical signals through different transmission media, such as:

* Ethernet cables
* Wireless networks (Wi-Fi)
* Optical fiber

Its primary function is to convert binary data into signals and transmit them across the network.

---

## Key Takeaways

* The OSI Model provides a standardized framework for understanding network communication.
* Each of the seven layers performs a specific function.
* TCP provides reliable, connection-oriented communication, while UDP provides faster, connectionless communication.
* IP addresses are used for logical addressing, whereas MAC addresses are used for physical addressing.
* Understanding the OSI Model helps SOC Analysts troubleshoot network issues and analyze network traffic effectively.
</p>

<hr>

# Encapsulation and Decapsulation

## Encapsulation

As data moves down through each layer of the OSI Model, every layer adds its own information to the data. This additional information contains details specific to that layer, allowing the receiving device to process the data correctly.

This process is known as **encapsulation**.

The name of the data changes as it moves through the layers:

| OSI Layer          | Data Unit                      |
| ------------------ | ------------------------------ |
| Application Layer  | Data                           |
| Presentation Layer | Data                           |
| Session Layer      | Data                           |
| Transport Layer    | Segment (TCP) / Datagram (UDP) |
| Network Layer      | Packet                         |
| Data Link Layer    | Frame                          |
| Physical Layer     | Bits                           |

### Layer-by-Layer Process

* In the **Application**, **Presentation**, and **Session** layers, the information is simply referred to as **data**.
* When the data reaches the **Transport Layer**, it becomes:

  * **Segment** if **TCP** is used.
  * **Datagram** if **UDP** is used.
* At the **Network Layer**, the data is called a **packet**.
* At the **Data Link Layer**, the packet is encapsulated into a **frame** by adding both a **header** and a **trailer**. The trailer contains error-checking information that helps detect whether the data has been corrupted during transmission.
* Finally, at the **Physical Layer**, the frame is converted into **bits** and transmitted across the physical medium.

---

## Decapsulation

When the data reaches the destination device, the process is reversed.

As the data moves upward through the OSI layers, each layer removes the information (headers and, where applicable, the trailer) that was added during encapsulation. This continues until the original data reaches the **Application Layer**.

This reverse process is known as **decapsulation**.

---

## Key Takeaways

* **Encapsulation** is the process of adding protocol-specific information to data as it travels down the OSI Model.
* Each layer adds its own header, while the **Data Link Layer** adds both a header and a trailer.
* The trailer is primarily used for **error detection**, helping identify whether the frame has been corrupted during transmission.
* **Decapsulation** is the reverse process, where the receiving device removes the headers and trailer to recover the original data.

<img src = "https://github.com/kalyank24/SOC-Progress/blob/main/Introdcutory%20Networking/images/Encapsulation.png" alt ="Encapsulation">

<br>

# TCP/IP Model

## Overview

The **TCP/IP (Transmission Control Protocol/Internet Protocol) Model** is the foundation of modern networking and is widely used in real-world communication. While it is similar to the OSI Model, it simplifies the networking process into **four layers**.

## TCP/IP Layers

1. Application Layer
2. Transport Layer
3. Internet Layer
4. Network Interface Layer

### OSI Model vs. TCP/IP Model

| OSI Model    | TCP/IP Model      |
| ------------ | ----------------- |
| Application  | Application       |
| Presentation | Application       |
| Session      | Application       |
| Transport    | Transport         |
| Network      | Internet          |
| Data Link    | Network Interface |
| Physical     | Network Interface |

Just like the OSI Model, the TCP/IP Model follows the processes of **encapsulation** and **decapsulation**.

* During **encapsulation**, each layer adds its own protocol-specific header to the data before passing it to the next layer.
* During **decapsulation**, the receiving device removes these headers layer by layer until the original data reaches the application.

---

# TCP Three-Way Handshake

When discussing the TCP/IP Model, we are also referring to a **suite of communication protocols**. One of the most important protocols is **TCP (Transmission Control Protocol)**.

TCP is a **connection-oriented protocol**, meaning it establishes a reliable connection between the sender and receiver before transmitting data.

This connection is established through a process called the **TCP Three-Way Handshake**.

## Steps of the Three-Way Handshake

### Step 1 – SYN

The client initiates the connection by sending a **SYN (Synchronize)** packet to the server.

### Step 2 – SYN + ACK

The server acknowledges the client's request by responding with a **SYN + ACK (Synchronize + Acknowledge)** packet.

### Step 3 – ACK

The client sends an **ACK (Acknowledge)** packet back to the server, completing the handshake and establishing the connection.

Once the connection is established, data transmission begins.

Because TCP is a reliable protocol, any data that is lost or corrupted during transmission is retransmitted, ensuring accurate and complete delivery.

---

# Ping

The **ping** command is a basic network diagnostic tool used to verify whether a remote host or device is reachable over a network.

It can also be used to test connectivity with other devices on a local network, provided they are configured to respond to ICMP requests.

## Protocol Used

The `ping` command uses the **Internet Control Message Protocol (ICMP)**.

* **OSI Model:** Network Layer
* **TCP/IP Model:** Internet Layer

## Basic Syntax

```bash
ping <target>
```

**Example:**

```bash
ping google.com
```

## How Ping Works

When a ping command is executed, the system sends **ICMP Echo Request** packets to the target host.

If the target is reachable and configured to respond, it replies with **ICMP Echo Reply** packets. The output typically includes:

* IP address of the target
* Round-trip time (latency)
* Number of packets sent and received
* Packet loss
* Time To Live (TTL)

When a domain name (such as `google.com`) is used, the system first resolves the domain to its corresponding IP address using DNS before sending the ICMP packets.

Since `ping` is included with almost every operating system, it is one of the most commonly used tools for basic network troubleshooting.

---

## Key Takeaways

* The TCP/IP Model is the practical networking model used on modern networks.
* It consists of four layers: Application, Transport, Internet, and Network Interface.
* Encapsulation and decapsulation work similarly to the OSI Model.
* TCP establishes reliable communication using the **Three-Way Handshake** (SYN → SYN/ACK → ACK).
* The `ping` command uses ICMP to test network connectivity and measure response times.


<br>

# Traceroute

**Traceroute** can be used to map the path your request takes as it heads to the destination. If we enter a website, the request will pass through several servers. Traceroute allows you to see those connections. It enables you to view every intermediate step between your computer and the resource that you requested.

## Basic Syntax

**Unix:**

```bash
traceroute <destination>
```

**Windows:**

```cmd
tracert <destination>
```

In Unix, it operates over **UDP**. In Windows, it operates similarly to the **ping** utility, using the **ICMP** protocol.

Initially, any request you make passes through the gateway. Traceroute returns information such as the number of hops it took to reach the destination and the time taken to reach each hop.


