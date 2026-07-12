# CSCE-3530-Network-Project
CSCE 3530 Network Project

Yuvraj Bains | EUID: yb0285 | CSCE 3530.401

Project Overview

This project builds and tests a small school computer lab network using GNS3, combined with live protocol captures from a real network stack to demonstrate core networking concepts. The lab network consists of a switch and four client PCs on a shared subnet. Additional protocol demonstrations — DHCP, DNS, HTTP/TCP, and ARP/ICMP — were captured directly from a live host network interface using Wireshark, since a Cisco IOS router image was not available for this environment.

Network Topology (GNS3 Lab)
<img width="626" height="389" alt="image" src="https://github.com/user-attachments/assets/ad5b460b-7414-4b18-af26-9d0d6fc10d68" />



DeviceIP AddressPurposeSwitch1—Layer 2 switching, connects all lab PCsPC1192.168.10.101/24Student PC (VPCS)PC2192.168.10.102/24Student PC (VPCS)PC3192.168.10.103/24Student PC (VPCS)PC4192.168.10.104/24Student PC (VPCS)

Implemented and Demonstrated Protocols

ProtocolWhere DemonstratedMethodICMPGNS3 lab + host captureping between GNS3 PCs; Wireshark capture of real ping to default gatewayARPHost captureWireshark capture showing ARP request/reply resolving gateway MAC addressDHCPHost captureipconfig /release + /renew, captured full DORA exchange (Discover, Offer, Request, Ack) in WiresharkDNSHost capturenslookup google.com, captured query/response over UDP in WiresharkHTTPHost captureLocal Python HTTP server + browser request, captured GET/200 OK exchange in WiresharkTCPHost captureSame HTTP capture, showing full three-way handshake (SYN, SYN-ACK, ACK) before the HTTP exchangeNATDesign only (not live)Planned as part of router configuration; not demonstrated live due to lack of available Cisco IOS image (see Limitations)

Testing Results


Successful ping connectivity confirmed between all four PCs on the GNS3 switch (192.168.10.101–104)
DHCP: real Discover/Offer/Request/Ack sequence captured, confirming full four-step DHCP exchange
DNS: real query and response captured for google.com, confirming UDP-based name resolution
HTTP/TCP: real GET request and 200 OK response captured, with visible TCP handshake preceding the HTTP exchange, and a 404 response captured for a missing resource
ARP/ICMP: ARP broadcast requests observed resolving gateway MAC address, followed by ICMP echo request/reply pairs with matching sequence numbers


Repository Structure

screenshots/
    GNS3 topology and console screenshots
captures/
    dhcp_capture.pcapng
    dns_capture.pcapng
    http_tcp_capture.pcapng
    arp_icmp_capture.pcapng
doc/
    Final project report (PDF)
README.md

Limitations and Challenges

This project was originally designed around a Cisco IOS router providing DHCP, DNS, HTTP, and NAT services within GNS3, as outlined in the original project proposal. During implementation, several environment-specific obstacles prevented that design from being fully realized in GNS3:


No Cisco IOS or IOU router image was available for import into GNS3
The host machine's ARM processor architecture is incompatible with VirtualBox/Docker-based virtualization (VBOX_E_PLATFORM_ARCH_NOT_SUPPORTED), which ruled out using the GNS3 VM or Docker containers as a software router/server alternative
GNS3's Cloud node, used to bridge the lab to a real network for DHCP/NAT testing, was not able to pass traffic reliably over the host's Wi-Fi adapter, a known limitation of Wi-Fi driver support on Windows


To still meet the project's protocol demonstration requirements, equivalent live protocol behavior (DHCP, DNS, HTTP, TCP, ARP, ICMP) was captured directly from the host machine's real network stack using Wireshark, providing genuine, unmodified protocol exchanges in place of software-emulated ones. NAT was not demonstrated live and is documented as a design-level component only.
