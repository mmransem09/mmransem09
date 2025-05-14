# Packet Filtering Lab

### 📘 Overview
This project was completed as part of a Network Security (NetSec) lab, focusing on internetwork design and packet filtering using firewall rules. The objective was to implement a secure internetwork for an imaginary organization by simulating an OpenBSD virtual lab environment and configuring routers and hosts using subnetting, NAT, and filtering policies.

---

### 🌐 Network Topology
The virtual internetwork was designed using a predefined topology consisting of multiple routers, bridges, and clients. The key components included:

Internal clients and servers (e.g., c1–c7, s1–s7)

Edge routers (rt1, rt2)

External nodes (ert3, ec8, es7)

---

### 🧩 IP Addressing Scheme
**Internal Network:** Subnetted from 192.168.0.0/24 to address all internal hosts and interfaces.

**External Connections:**

rt2 ↔ ert3: 1.2.3.0/24 (rt2: 1.2.3.4)

ert3 ↔ ec8: 2.2.3.0/24 (ert3: .3, ec8: .8)

ert3 ↔ es7: 3.2.3.0/24 (ert3: .3, es7: .8)

---

### 🔒 Security Requirements and Implementation
The organization adopted a default deny firewall policy. All traffic was blocked unless explicitly allowed. Packet filtering rules were applied on rt1 and rt2, with rt2 also performing Network Address Translation (NAT) for external communication.

### 🔐  Services and Access Rules
 
**Public Access (From Internet to Internal):**

s5 – HTTPS server: accessible via TCP 443

s6 – SMTP server: accessible via TCP 25; internal users also access it via IMAP (TCP 143)

s7 – DNS server: accessible via UDP/TCP 53

**Internal Access (To Internet):**

Web browsing: internal clients access HTTP/HTTPS (TCP 80/443)

SMTP: internal clients send email via s1 (SMTP relay) and s6

DNS: internal clients query s2 (internal resolver), which forwards to public DNS servers and s7

FTP: internal clients use FTP via a proxy on rt2 to access internal (s5) and external (es7) FTP servers

---

### 🔁 NAT Configuration
All outbound connections from the internal network were NATed using the IP address 1.2.3.4 on the external interface of rt2.

Port forwarding rules were configured for public-facing services hosted internally.

---

### 🛠️ Tools and Testing
**netcat (nc):** Used to emulate client-server communication for HTTP, SMTP, DNS, and IMAP testing.

**ftp:** Actual FTP servers were configured on s5 and es7. Access was managed through an FTP proxy running on rt2.

---

### 📦 Deliverables
🗺️ Topology Diagram: Includes all IP addresses, subnets, and network components. (Include this as an image or diagram file in your GitHub repo.)

📜 Firewall Rulesets: Detailed iptables or equivalent configuration scripts applied on rt1 and rt2.

📄 Testing Logs: Connection tests and verification for each service scenario using netcat, ftp, and other diagnostic tools.

---

### ✅ Conclusion
This project provided hands-on experience in network segmentation, firewall policy design, NAT configuration, and service access control. It reinforced my understanding of core cybersecurity principles by applying a least-privilege access model to real-world networking scenarios.
