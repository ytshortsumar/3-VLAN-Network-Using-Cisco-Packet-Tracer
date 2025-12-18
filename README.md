# 3-VLAN Network Configuration Using Cisco Packet Tracer

## 📘 Project Overview
This lab demonstrates the design and implementation of a **3-VLAN switched network** using **Cisco Packet Tracer**.  
The network is built from scratch using **three Cisco 2960 switches** and **six PCs**, segmented into three logical groups using VLANs.

The objective of this project is to understand:
- VLAN creation and management
- Trunk and access port configuration
- Network segmentation for security and traffic isolation
- End-to-end connectivity testing within the same VLAN

---

## 🎯 Lab Objectives
- Create and configure **three VLANs**
- Assign end devices to their respective VLANs
- Configure **trunk links** between switches
- Verify VLAN-based communication
- Ensure **inter-VLAN communication is blocked** (no router used)

---

## 🧱 Network Topology

### VLAN Structure
| VLAN ID | VLAN Name | Group   |
|-------:|-----------|---------|
| 10     | STUDENTS  | Students |
| 20     | FACULTY   | Faculty  |
| 30     | GUEST     | Guests   |

### Devices Used
- **3 × Cisco 2960 Switches**
- **6 × PCs**

---

## 🔌 Physical Setup

### Switch Placement
- **Switch 1** → Center (Core switch)
- **Switch 2** → Left
- **Switch 3** → Right

### PC Placement
- **Switch 2**: PC1, PC2, PC3
- **Switch 3**: PC4, PC5, PC6

### Cabling
- **Switch-to-Switch**: Copper Cross-Over
- **PC-to-Switch**: Copper Straight-Through

| Connection Type | From | To | Ports |
|-----------------|------|----|-------|
| Trunk | Switch 1 | Switch 2 | Fa0/1 ↔ Fa0/1 |
| Trunk | Switch 1 | Switch 3 | Fa0/2 ↔ Fa0/2 |
| Access | PC1 | Switch 2 | Fa0/2 |
| Access | PC2 | Switch 2 | Fa0/3 |
| Access | PC3 | Switch 2 | Fa0/4 |
| Access | PC4 | Switch 3 | Fa0/1 |
| Access | PC5 | Switch 3 | Fa0/3 |
| Access | PC6 | Switch 3 | Fa0/4 |

---

## 🌐 IP Addressing Scheme

### VLAN 10 – Students
- PC1 → `192.168.10.2 /24`
- PC4 → `192.168.10.4 /24`

### VLAN 20 – Faculty
- PC2 → `192.168.20.2 /24`
- PC5 → `192.168.20.3 /24`

### VLAN 30 – Guests
- PC3 → `192.168.30.2 /24`
- PC6 → `192.168.30.3 /24`

> No default gateway is required as routing is not implemented.

---

## ⚙️ Switch Configuration

### Switch 1 (Core Switch)
- VLANs 10, 20, 30 created
- Ports Fa0/1 and Fa0/2 configured as **trunks**

### Switch 2 (Left)
- VLANs created
- Fa0/1 configured as trunk
- Access ports:
  - Fa0/2 → VLAN 10
  - Fa0/3 → VLAN 20
  - Fa0/4 → VLAN 30

### Switch 3 (Right)
- VLANs created
- Fa0/2 configured as trunk
- Access ports:
  - Fa0/1 → VLAN 10
  - Fa0/3 → VLAN 20
  - Fa0/4 → VLAN 30

---

## ✅ Verification & Testing

### Successful Tests
- **Student VLAN**: PC1 → PC4 ✔
- **Guest VLAN**: PC3 → PC6 ✔

### Security Test
- **Guest → Faculty** (PC3 → PC2) ❌  
  Result: *Request Timed Out* (Expected behavior)

---

## 📂 Files Included
- `3-Switch-VLAN-System.pkt` – Cisco Packet Tracer lab file
- `README.md` – Project documentation

---

## 🧠 Key Learning Outcomes
- Practical VLAN implementation
- Trunk vs Access port understanding
- Network segmentation without routing
- Real-world Layer 2 network design

---

## 🛠 Tools Used
- Cisco Packet Tracer
- Cisco 2960 Switches

---

## 👤 Author
**Umar Farooq**  
Networking Lab Assignment  
