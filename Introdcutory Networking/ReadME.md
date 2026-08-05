
<h1>Introductry Networking</h1>

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
