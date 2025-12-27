# Network Traffic Analysis & Protocol Dissection (Wireshark)

## Technical Objective: Deep Packet Inspection for Incident Response

---

## Scenario
As a security analyst, I was tasked with investigating a network capture to identify specific communication patterns between internal and external assets. Using Wireshark, I performed a deep dive into the OSI layers—from MAC addresses at the Data Link layer to application-specific protocols like DNS and HTTP—to verify traffic integrity and search for indicators of compromise (IoC).

## 1. Task 1: Initial Traffic Ingestion & Global Overview

This task was about loading the data and getting a basic view of the traffic.

1.  **Open the Capture File:** Double-clicked the `sample.pcap` file to open it in Wireshark.
2.  **Check Packet Summary:** Looked at the main columns (No., Time, Source, Destination, Protocol, Length, Info) for a general overview.
3.  **Note Colors:** Observed that different protocols had distinct colors (e.g., light green for **TCP/HTTP**).

---

## 2. Task 2: TCP/IP Layer Analysis & Handshake Verification

This task focused on using the first filter and inspecting the deep structure of a single packet.

1.  **Filter by IP Address (General):** Entered the filter `ip.addr == 142.250.1.139` to narrow the view to traffic involving that IP.
2.  **Inspect a Packet:** Double-clicked the first **TCP** packet to open the detailed inspection window.
3.  **Unwrap the Layers:** Expanded the subtrees to view the packet's structure: **Frame**, **Ethernet II**, **Internet Protocol Version 4**, and **Transmission Control Protocol**.
4.  **Check TCP Flags:** Expanded the **Flags** section under TCP to see the connection status details.
5.  **Clear Filter:** Clicked the 'X Clear display filter' icon.

---

## 3. Task 3: Hardware-Level Tracking & Source Attribution

This task involved using more specific filters to track traffic by source or hardware address.

1.  **Filter by IP Source:** Entered the filter `ip.src == 142.250.1.139` to see only packets coming *from* that IP.
2.  **Clear Filter:** Clicked the 'X Clear display filter' icon.
3.  **Filter by MAC Address:** Entered the filter `eth.addr == 42:01:ac:15:e0:02` to find traffic related to a specific hardware address.
4.  **Inspect MAC Data:** Double-clicked the first packet and expanded **Ethernet II** to verify the MAC address filter worked.
5.  **Clear Filter:** Clicked the 'X Clear display filter' icon.

---

## 4. Task 4 & 5: Application Layer Forensics & Payload Inspection

This final section covered how to analyze application-specific protocols and search the raw data.

1.  **Filter for DNS:** Entered the filter `udp.port == 53` to isolate all DNS lookups.
2.  **Inspect DNS Query:** Double-clicked a DNS packet and expanded the **Domain Name System (query)** subtree to find the website name requested (`opensource.google.com`).
3.  **Filter for HTTP:** Entered the filter `tcp.port == 80` to find unencrypted web traffic.
4.  **Search the Data Payload:** Entered the content search filter `tcp contains "curl"` to find packets that included that specific text string in the data section.

---
## What I Learned
- Protocol Hierarchies: Gained hands-on experience navigating the encapsulated layers of a packet, specifically focusing on TCP flags and DNS query structures.

- Filtering Logic: Mastered the use of Wireshark display filters (ip.addr, eth.addr, udp.port) to isolate targeted traffic in high-volume captures.

- Payload Forensics: Learned to use content string searches (e.g., tcp contains "curl") to identify specific tools or commands used within the network stream.

- Logical Troubleshooting: Applied a systematic approach to decapsulating traffic to find the "who, what, and where" of a network event.

---

* **Author:** Joan

---
