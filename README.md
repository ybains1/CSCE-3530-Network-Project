# CSCE-3530-Network-Project
CSCE 3530 Network Project

Yuvraj Bains | EUID: yb0285 | CSCE 3530.401

Project Overview

This project builds and tests a small school computer lab network using GNS3, combined with live protocol captures from a real network stack to demonstrate core networking concepts. The lab network consists of a switch and four client PCs on a shared subnet. Additional protocol demonstrations — DHCP, DNS, HTTP/TCP, and ARP/ICMP — were captured directly from a live host network interface using Wireshark, since a Cisco IOS router image was not available for this environment.

Network Topology (GNS3 Lab)

#mermaid-r3dd-r1 { font-family: "Anthropic Sans", system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; font-size: 16px; fill: rgb(229, 229, 229); }
#mermaid-r3dd-r1 .edge-animation-slow { stroke-dashoffset: 900; animation: 50s linear 0s infinite normal none running dash; stroke-linecap: round; stroke-dasharray: 9, 5 !important; }
#mermaid-r3dd-r1 .edge-animation-fast { stroke-dashoffset: 900; animation: 20s linear 0s infinite normal none running dash; stroke-linecap: round; stroke-dasharray: 9, 5 !important; }
#mermaid-r3dd-r1 .error-icon { fill: rgb(204, 120, 92); }
#mermaid-r3dd-r1 .error-text { fill: rgb(51, 135, 163); stroke: rgb(51, 135, 163); }
#mermaid-r3dd-r1 .edge-thickness-normal { stroke-width: 1px; }
#mermaid-r3dd-r1 .edge-thickness-thick { stroke-width: 3.5px; }
#mermaid-r3dd-r1 .edge-pattern-solid { stroke-dasharray: 0; }
#mermaid-r3dd-r1 .edge-thickness-invisible { stroke-width: 0; fill: none; }
#mermaid-r3dd-r1 .edge-pattern-dashed { stroke-dasharray: 3; }
#mermaid-r3dd-r1 .edge-pattern-dotted { stroke-dasharray: 2; }
#mermaid-r3dd-r1 .marker { fill: rgb(161, 161, 161); stroke: rgb(161, 161, 161); }
#mermaid-r3dd-r1 .marker.cross { stroke: rgb(161, 161, 161); }
#mermaid-r3dd-r1 svg { font-family: "Anthropic Sans", system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; font-size: 16px; }
#mermaid-r3dd-r1 p { margin: 0px; }
#mermaid-r3dd-r1 .label { font-family: "Anthropic Sans", system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; color: rgb(229, 229, 229); }
#mermaid-r3dd-r1 .cluster-label text { fill: rgb(51, 135, 163); }
#mermaid-r3dd-r1 .cluster-label span { color: rgb(51, 135, 163); }
#mermaid-r3dd-r1 .cluster-label span p { background-color: transparent; }
#mermaid-r3dd-r1 .label text, #mermaid-r3dd-r1 span { fill: rgb(229, 229, 229); color: rgb(229, 229, 229); }
#mermaid-r3dd-r1 .node rect, #mermaid-r3dd-r1 .node circle, #mermaid-r3dd-r1 .node ellipse, #mermaid-r3dd-r1 .node polygon, #mermaid-r3dd-r1 .node path { fill: transparent; stroke: rgb(161, 161, 161); stroke-width: 1px; }
#mermaid-r3dd-r1 .rough-node .label text, #mermaid-r3dd-r1 .node .label text, #mermaid-r3dd-r1 .image-shape .label, #mermaid-r3dd-r1 .icon-shape .label { text-anchor: middle; }
#mermaid-r3dd-r1 .node .katex path { fill: rgb(0, 0, 0); stroke: rgb(0, 0, 0); stroke-width: 1px; }
#mermaid-r3dd-r1 .rough-node .label, #mermaid-r3dd-r1 .node .label, #mermaid-r3dd-r1 .image-shape .label, #mermaid-r3dd-r1 .icon-shape .label { text-align: center; }
#mermaid-r3dd-r1 .node.clickable { cursor: pointer; }
#mermaid-r3dd-r1 .root .anchor path { stroke-width: 0; stroke: rgb(161, 161, 161); fill: rgb(161, 161, 161) !important; }
#mermaid-r3dd-r1 .arrowheadPath { fill: rgb(11, 11, 11); }
#mermaid-r3dd-r1 .edgePath .path { stroke: rgb(161, 161, 161); stroke-width: 1px; }
#mermaid-r3dd-r1 .flowchart-link { stroke: rgb(161, 161, 161); fill: none; }
#mermaid-r3dd-r1 .edgeLabel { background-color: transparent; text-align: center; }
#mermaid-r3dd-r1 .edgeLabel p { background-color: transparent; }
#mermaid-r3dd-r1 .edgeLabel rect { opacity: 0.5; background-color: transparent; fill: transparent; }
#mermaid-r3dd-r1 .labelBkg { background-color: rgba(0, 0, 0, 0.5); }
#mermaid-r3dd-r1 .cluster rect { fill: rgb(204, 120, 92); stroke: rgb(138, 115, 107); stroke-width: 1px; }
#mermaid-r3dd-r1 .cluster text { fill: rgb(51, 135, 163); }
#mermaid-r3dd-r1 .cluster span { color: rgb(51, 135, 163); }
#mermaid-r3dd-r1 div.mermaidTooltip { position: absolute; text-align: center; max-width: 200px; padding: 2px; font-family: "Anthropic Sans", system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; font-size: 12px; background: rgb(204, 120, 92); border: 1px solid rgb(138, 115, 107); border-radius: 2px; pointer-events: none; z-index: 100; }
#mermaid-r3dd-r1 .flowchartTitleText { text-anchor: middle; font-size: 18px; fill: rgb(229, 229, 229); }
#mermaid-r3dd-r1 rect.text { fill: none; stroke-width: 0; }
#mermaid-r3dd-r1 .icon-shape, #mermaid-r3dd-r1 .image-shape { background-color: transparent; text-align: center; }
#mermaid-r3dd-r1 .icon-shape p, #mermaid-r3dd-r1 .image-shape p { background-color: transparent; padding: 2px; }
#mermaid-r3dd-r1 .icon-shape .label rect, #mermaid-r3dd-r1 .image-shape .label rect { opacity: 0.5; background-color: transparent; fill: transparent; }
#mermaid-r3dd-r1 .label-icon { display: inline-block; height: 1em; overflow: visible; vertical-align: -0.125em; }
#mermaid-r3dd-r1 .node .label-icon path { fill: currentcolor; stroke: revert; stroke-width: revert; }
#mermaid-r3dd-r1 .node .neo-node { stroke: rgb(161, 161, 161); }
#mermaid-r3dd-r1 [data-look="neo"].node rect, #mermaid-r3dd-r1 [data-look="neo"].cluster rect, #mermaid-r3dd-r1 [data-look="neo"].node polygon { stroke: url("#mermaid-r3dd-r1-gradient"); filter: drop-shadow(rgb(185, 185, 185) 1px 2px 2px); }
#mermaid-r3dd-r1 [data-look="neo"].node path { stroke: url("#mermaid-r3dd-r1-gradient"); stroke-width: 1px; }
#mermaid-r3dd-r1 [data-look="neo"].node .outer-path { filter: drop-shadow(rgb(185, 185, 185) 1px 2px 2px); }
#mermaid-r3dd-r1 [data-look="neo"].node .neo-line path { stroke: rgb(161, 161, 161); filter: none; }
#mermaid-r3dd-r1 [data-look="neo"].node circle { stroke: url("#mermaid-r3dd-r1-gradient"); filter: drop-shadow(rgb(185, 185, 185) 1px 2px 2px); }
#mermaid-r3dd-r1 [data-look="neo"].node circle .state-start { fill: rgb(0, 0, 0); }
#mermaid-r3dd-r1 [data-look="neo"].icon-shape .icon { fill: url("#mermaid-r3dd-r1-gradient"); filter: drop-shadow(rgb(185, 185, 185) 1px 2px 2px); }
#mermaid-r3dd-r1 [data-look="neo"].icon-shape .icon-neo path { stroke: url("#mermaid-r3dd-r1-gradient"); filter: drop-shadow(rgb(185, 185, 185) 1px 2px 2px); }
#mermaid-r3dd-r1 :root { --mermaid-font-family: "Anthropic Sans",system-ui,"Segoe UI",Roboto,Helvetica,Arial,sans-serif; }Switch1PC1192.168.10.101/24PC2192.168.10.102/24PC3192.168.10.103/24PC4192.168.10.104/24

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
