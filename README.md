# 🚀 Quality of Service (QoS) Implementation in a Multi-VLAN Network

## 📘 Project Overview

This project showcases a simulated enterprise-level network designed and implemented using **Cisco Packet Tracer**, with a focus on **Quality of Service (QoS)** to prioritize different types of traffic across VLANs. The network features voice-over-IP (VoIP), dynamic host configuration (DHCP), inter-VLAN routing, OSPF as the dynamic routing protocol, and simulated internet connectivity.

Although VoIP telephony is set up within the topology, this README and the accompanying report focus solely on network services and QoS.

---

## 🛠️ Functional Highlights

### 🔹 VLAN Segmentation

The network uses **Virtual LANs (VLANs)** to logically separate different types of traffic:
- One VLAN for regular data devices (PCs)
- Another VLAN dedicated to voice traffic (IP Phones)

This segmentation ensures organized traffic flow and lays the foundation for applying differentiated QoS policies.

### 🔹 Dynamic IP Allocation via DHCP

To automate network configuration for hosts:
- **Separate DHCP pools** are configured for each VLAN.
- PCs receive IP addresses, default gateway, and DNS information dynamically.
- IP Phones are also assigned their settings automatically, including a specific TFTP server for call manager registration.

This reduces administrative overhead and ensures consistency across devices.

### 🔹 Inter-VLAN Routing with Router-on-a-Stick

A single physical router interface is subdivided into **multiple subinterfaces**, each associated with a VLAN. This approach, known as **router-on-a-stick**, allows routing between VLANs while minimizing hardware usage.

### 🔹 OSPF as the Routing Protocol

The routers in the topology use **OSPF (Open Shortest Path First)**, a scalable and efficient interior gateway protocol. This enables dynamic discovery of routes between the internal LAN and the simulated internet, and allows for automatic adaptation in case of link failures.

---

## 🧩 Quality of Service (QoS) Implementation

QoS is the **core focus** of this project. A dedicated policy is applied to classify and prioritize traffic as follows:

- **Voice Traffic (RTP protocol):**  
  - Marked with high-priority DSCP value `EF (Expedited Forwarding)`
  - Guaranteed bandwidth with strict priority queuing

- **Web Traffic (HTTP):**  
  - Allocated a moderate amount of bandwidth
  - Marked with `AF31` (Assured Forwarding)

- **Ping/Diagnostic Traffic (ICMP):**  
  - Given minimal guaranteed bandwidth
  - Marked with `AF11`

These policies ensure that voice traffic receives minimal delay and jitter, even during periods of congestion, which is crucial for call quality.

The QoS policy is applied **outbound on the serial interface** connecting to the internet, simulating how enterprise networks manage upstream traffic quality.

---

## 🌐 Internet Simulation

To demonstrate end-to-end connectivity and DNS resolution:
- A **simulated internet** switch connects to servers representing popular domains like Google DNS, Cisco, and Facebook.
- These servers are manually configured and serve as test endpoints for ping and HTTP traffic.
- Internal hosts can access these servers through the routing and NAT mechanisms configured in the network.

---

## 🎯 Key Learnings

- Design and deploy a logically segmented network using VLANs
- Automate IP assignment with per-VLAN DHCP pools
- Apply inter-VLAN routing using subinterfaces
- Understand and configure QoS class maps, policy maps, and DSCP markings
- Implement OSPF for internal routing across a distributed topology
- Validate connectivity and performance prioritization using simulated services

---

## 🧪 How to Test

1. Open the `.pkt` file in Cisco Packet Tracer.
2. Power on the devices and observe the DHCP assignments.
3. Use the PC command prompt to:
   - Ping the internet servers.
   - Access websites via simulated HTTP.
4. Initiate simultaneous traffic (e.g., pings + web browsing + voice call) to test QoS behavior.
5. Observe DSCP markings and traffic priority using simulation mode.

---

## 📌 Notes

- The IP telephony configurations are present on Router3 but not covered in this README or the associated report.
- The QoS setup is designed to reflect real-world practices for managing voice and data convergence.
- This project is ideal for learning enterprise network design, especially for scenarios where performance tuning is essential.

---

## 👤 Author

**Het Patel**  
Project: Computer Networks – QoS and Routing Simulation  

---

## 📄 License

This project is open for educational use. Attribution appreciated!
