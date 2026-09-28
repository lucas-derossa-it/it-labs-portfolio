# TCP/IP and OSI Protocol Analysis in Cisco Packet Tracer

Hands-on Cisco Packet Tracer lab focused on observing how application, transport, network, and data-link protocols work together when a client accesses a web service.

## Lab Date

28 September 2026

## Objective

Investigate the TCP/IP protocol suite and OSI model in action by tracing a web request from a client to a server in Packet Tracer Simulation Mode.

The lab demonstrates how DNS resolves a hostname, TCP establishes a reliable connection, HTTP exchanges web data, IP provides logical addressing and routing, Ethernet transports frames on the local network, and NAT translates the client's private address when traffic crosses the router.

## Environment

- Cisco Packet Tracer
- Client: PC1
- Web/DNS Server: Server0
- Internal client IPv4: `192.168.0.3`
- Default gateway: `192.168.0.1`
- DNS / web server: `192.168.1.1`
- Router outside-facing IPv4 observed through NAT: `192.168.1.10`
- Test URL: `http://www.osi.local`

## What I Configured and Verified

- Restored valid DHCP addressing for PC1.
- Configured the DHCP service to provide the correct DNS server address.
- Enabled DNS service on Server0.
- Created an A record mapping `www.osi.local` to `192.168.1.1`.
- Verified successful hostname resolution and web access.
- Used Packet Tracer Simulation Mode to inspect DNS, TCP, HTTP, IP, Ethernet, and NAT behaviour.
- Compared inbound and outbound PDU details across the communication flow.

## Protocol Flow Observed

1. **DNS (Domain Name System)** resolved `www.osi.local` to `192.168.1.1`.
2. **UDP (User Datagram Protocol)** carried the DNS query using destination port `53`.
3. **TCP (Transmission Control Protocol)** established a connection from client source port `1026` to server destination port `80`.
4. **HTTP (Hypertext Transfer Protocol)** carried the web request and response.
5. **IP (Internet Protocol)** provided end-to-end logical addressing.
6. **Ethernet** provided Layer 2 frame delivery between local interfaces.
7. **NAT (Network Address Translation)** translated the internal client address `192.168.0.3` to the router-facing address `192.168.1.10` when crossing into the server network.
8. TCP later closed the session using `FIN+ACK`, with the client entering `FIN_WAIT_1`.

## Validation Results

- DHCP request: **Successful**
- DNS lookup: **Successful**
- DNS answer: `www.osi.local → 192.168.1.1`
- HTTP server port: `80`
- DNS server port: `53`
- TCP connection state: `ESTABLISHED`
- Web page load: **Successful**

## Skills Demonstrated

Cisco Packet Tracer, TCP/IP, OSI model, DNS, DHCP, TCP, UDP, HTTP, IPv4 addressing, Ethernet, NAT, port analysis, PDU inspection, simulation-mode troubleshooting, and structured network validation.

## Evidence

The lab evidence is organised as:

- `evidence/01-DNS-Query-www-osi-local.png`
- `evidence/02-DNS-Response-192-168-1-1.png`
- `evidence/03-TCP-HTTP-Port-80.png`
- `evidence/04-TCP-Connection-Established.png`
- `evidence/05-TCP-Connection-FIN-ACK.png`
- `evidence/06-HTTP-Webpage-Success.png`
- `packet-tracer/tcp-ip-osi-protocol-analysis.pka`

## Portfolio Summary

This lab demonstrates practical understanding of how multiple TCP/IP protocols cooperate during a real web transaction and how to troubleshoot connectivity by working through addressing, DNS resolution, transport-layer sessions, application traffic, and packet-level evidence.
