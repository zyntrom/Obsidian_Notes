## 📄 **1.7 DNS, DHCP, NAT, Firewalls**

### 🔹 DNS (Domain Name System)

Converts **domain ↔ IP**

🔥 DNS Exploitation Examples:

- DNS spoofing
- Cache poisoning
- DNS tunneling for exfiltration (covert C2 channel)

---

### 🔹 DHCP

Assigns:

- IP
- Gateway
- DNS
- Subnet mask

💀 DHCP Attack

- Rogue DHCP server → gives attacker gateway → MitM

---

### 🔹 NAT (Network Address Translation)

- Allows multiple LAN devices to use **one public IP**
- Hides internal IP range

📌 Hackers bypass NAT using:

- Reverse shells
- UPnP abuse
- Port forwarding via malware

---

### 🔹 Firewalls

|Type|Restricts|
|---|---|
|Network|IPs, ports|
|Application|URLs, signatures, payloads (WAF)|

Hacker thinking:

- Scan allowed ports → exploit allowed services
- Use **tunneled traffic** to bypass firewall (DNS, HTTPS, ICMP)

---

### 🔹 Proxies

Used for anonymity and traffic filtering

💀 Attack uses:

- Proxy chaining for anonymity
- Bypass corporate firewalls using public proxies/VPN/TOR