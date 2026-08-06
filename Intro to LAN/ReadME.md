
# LAN Topologies

**Topology** refers to the network infrastructure, describing how devices are connected within a network. It provides a logical representation of the network layout and the communication between devices.

There are four main types of LAN topologies:

1. Star Topology
2. Bus Topology
3. Ring Topology
4. Mesh Topology

---

## 1. Star Topology

In a **Star Topology**, all devices are connected to a central device, which is usually a **switch** or a **hub**.

This topology requires additional networking equipment and more cabling than some other topologies.

If a single device fails or becomes disconnected, only that device is affected, and the rest of the network continues to function normally. However, if the central device fails, the entire network goes down, disrupting all communication.

Due to the additional equipment and cabling required, the Star Topology is more expensive than other topologies.

---

## 2. Bus Topology

In a **Bus Topology**, all devices are connected to a single cable known as the **backbone** or **bus**. Data travels through this backbone to reach the intended device.

Adding or removing devices is easier compared to other topologies and usually does not interrupt the network.

If a single device fails, only that device loses connectivity. However, if the backbone cable is damaged, the entire network becomes unavailable.

The overall efficiency of a Bus Topology is lower than other topologies, making it suitable only for small networks. It is cost-effective because it requires less cabling and has lower maintenance costs.

---

## 3. Ring Topology

In a **Ring Topology**, devices are connected in a circular manner, forming a closed loop. Each device is connected to the next device, and the last device is connected back to the first.

This topology requires less cabling and no additional networking equipment, making it cost-effective.

However, if any device or connection in the ring fails, the entire network communication is disrupted.

---

## 4. Mesh Topology

In a **Mesh Topology**, every device is connected to every other device in the network.

If one connection fails, the data can travel through an alternative path, making the network highly reliable.

However, Mesh Topology requires significantly more cabling than other topologies, making installation and troubleshooting more difficult. It is also the most expensive topology to implement.

---

# Switch

A **switch** is a networking device used to connect multiple devices, such as computers, printers, and other network-enabled devices, using Ethernet cables.

Switches typically contain multiple LAN ports, ranging from **8 to 64 ports**, depending on the model.

Unlike a hub, a switch forwards data only to the intended destination device, reducing unnecessary network traffic and improving overall network performance.

Switches are commonly used in small businesses, schools, offices, and other environments where multiple devices need to communicate on the same network.

Multiple switches and routers can also be connected together. This reduces network redundancy and allows data to travel through multiple paths. If one path becomes unavailable, the data can be routed through an alternative path.

---

# Router

A **router** is a networking device used to connect different networks and enable communication between them.

**Routing** is the process of forwarding data between networks by determining the best available path. This ensures that data is delivered successfully from the source network to the destination network.
