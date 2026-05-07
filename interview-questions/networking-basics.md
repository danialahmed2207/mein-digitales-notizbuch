# Networking Basics — Interview Questions

> Common interview questions for networking and connectivity troubleshooting roles.

---

## 1. OSI Model

**Q: Name the seven layers of the OSI model and give an example for each.**

**A:**
1. Physical — cables, hubs, NICs
2. Data Link — switches, MAC addresses, Ethernet
3. Network — routers, IP addresses, ICMP
4. Transport — TCP, UDP, ports
5. Session — session management, NetBIOS
6. Presentation — SSL/TLS, encoding
7. Application — HTTP, DNS, SSH, FTP

**Q: What is the difference between TCP and UDP?**

**A:** TCP is connection-oriented, reliable, and ordered (used for HTTP, SSH). UDP is connectionless, fast, and does not guarantee delivery (used for DNS, streaming, VoIP).

## 2. IP Addressing

**Q: What is the difference between IPv4 and IPv6?**

**A:** IPv4 uses 32-bit addresses (e.g., `192.168.1.1`) and supports ~4.3 billion addresses. IPv6 uses 128-bit addresses (e.g., `2001:0db8::1`) and provides a vastly larger address space, built-in security, and eliminates the need for NAT.

**Q: What is a subnet mask and how does CIDR work?**

**A:** A subnet mask divides an IP address into network and host portions. CIDR notation (e.g., `/24`) represents the number of network bits. `/24` equals `255.255.255.0` and provides 254 usable host addresses.

## 3. DNS & DHCP

**Q: Explain how DNS resolution works.**

**A:** A client queries a resolver, which checks its cache. If not cached, it queries the root server, then the TLD server (e.g., `.com`), then the authoritative nameserver, which returns the IP address.

**Q: What is DHCP and how does it work?**

**A:** DHCP automatically assigns IP addresses. The process is DORA: Discover, Offer, Request, Acknowledge.

## 4. Troubleshooting

**Q: A user cannot access the internet. Walk me through your troubleshooting steps.**

**A:**
1. Check physical connection (cable, Wi-Fi)
2. Verify IP configuration (`ip addr`)
3. Check default gateway (`ip route`)
4. Ping the gateway
5. Ping an external IP (`8.8.8.8`)
6. Test DNS resolution (`nslookup google.com`)
7. Check firewall rules (`iptables -L`)

**Q: What is the difference between a hub, switch, and router?**

**A:** A hub broadcasts traffic to all ports. A switch forwards traffic based on MAC addresses to specific ports. A router forwards traffic between networks based on IP addresses.

## 5. Common Ports

**Q: What are the default ports for SSH, HTTP, HTTPS, DNS, and SMTP?**

**A:**
- SSH: 22
- HTTP: 80
- HTTPS: 443
- DNS: 53
- SMTP: 25

---

## Practice Tip

Draw the OSI model and map protocols to layers. Interviewers often ask you to whiteboard this.
