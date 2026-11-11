# Task 5: Network Traffic Analysis Using Wireshark

## Overview
This repository contains Task 5: Capture and Analyze Network Traffic Using Wireshark, completed as part of the Cyber Security Internship.

The objective was to capture live network traffic on Kali Linux and analyze DNS, ICMP, TCP, and HTTP protocols.

## Environment & Tools
- **Operating System:** Kali Linux
- **Network Interface:** `eth0`
- **Tools Used:** Wireshark v4.6.x, `curl`, `ping`

## Steps Performed

1. Started live packet capture on the active interface using Wireshark.
2. Generated network traffic using the following commands:

   - `ping -c 4 8.8.8.8` – Generated ICMP traffic.
   - `curl -I http://neverssl.com` – Generated DNS queries and TCP connection attempts.
   - `curl -I http://example.com` – Generated TCP and HTTP traffic.

3. Stopped the capture and exported it as `network_traffic.pcap`.
4. Applied Wireshark display filters to analyze different protocols.
5. Inspected packet headers, connection details, and server responses.

## Protocols Identified & Key Findings

| Protocol | Layer | Display Filter | Key Findings |
|---|---|---|---|
| DNS | Application | `dns` | Successfully resolved `neverssl.com` and `example.com` through the local DNS resolver. |
| ICMP | Network | `icmp` | Captured 4 Echo Requests and 4 Echo Replies from `8.8.8.8`, with 0% packet loss. |
| TCP | Transport | `tcp` | Identified the three-way handshake (SYN, SYN-ACK, ACK) and graceful connection termination using FIN-ACK. |
| HTTP | Application | `http` | Captured an HTTP HEAD request and received an `HTTP/1.1 200 OK` response. |

## Detailed Observations

### 1. DNS Analysis
- Applied the `dns` filter.
- Observed DNS queries and responses.
- Verified the resolution of `neverssl.com` and `example.com`.

### 2. ICMP Analysis
- Applied the `icmp` filter.
- Captured 4 Echo Requests and 4 Echo Replies.
- Observed 0% packet loss and approximately 18.8 ms latency.

### 3. TCP Analysis
- Applied the `tcp` filter.
- Identified the TCP three-way handshake:
  - SYN
  - SYN-ACK
  - ACK
- Observed graceful connection termination using FIN-ACK packets.

### 4. HTTP Analysis
- Applied the `http` filter.
- Identified the client HTTP HEAD request.
- Observed the server response: `HTTP/1.1 200 OK`.

