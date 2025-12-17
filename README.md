# Wireshark Lab: Step-by-Step Procedure

This guide documents the exact actions and commands used in the "Analyze your first packet with Wireshark" lab, broken down into the four main tasks.

---

## 1. Task 1: Opening the File and Overview

This task was about loading the data and getting a basic view of the traffic.

1.  **Open the Capture File:** Double-clicked the `sample.pcap` file to open it in Wireshark.
2.  **Check Packet Summary:** Looked at the main columns (No., Time, Source, Destination, Protocol, Length, Info) for a general overview.
3.  **Note Colors:** Observed that different protocols had distinct colors (e.g., light green for **TCP/HTTP**).

---

## 2. Task 2: Basic Filtering and Packet Layers

This task focused on using the first filter and inspecting the deep structure of a single packet.

1.  **Filter by IP Address (General):** Entered the filter `ip.addr == 142.250.1.139` to narrow the view to traffic involving that IP.
2.  **Inspect a Packet:** Double-clicked the first **TCP** packet to open the detailed inspection window.
3.  **Unwrap the Layers:** Expanded the subtrees to view the packet's structure: **Frame**, **Ethernet II**, **Internet Protocol Version 4**, and **Transmission Control Protocol**.
4.  **Check TCP Flags:** Expanded the **Flags** section under TCP to see the connection status details.
5.  **Clear Filter:** Clicked the 'X Clear display filter' icon.

---

## 3. Task 3: Focused Filters (IP and MAC)

This task involved using more specific filters to track traffic by source or hardware address.

1.  **Filter by IP Source:** Entered the filter `ip.src == 142.250.1.139` to see only packets coming *from* that IP.
2.  **Clear Filter:** Clicked the 'X Clear display filter' icon.
3.  **Filter by MAC Address:** Entered the filter `eth.addr == 42:01:ac:15:e0:02` to find traffic related to a specific hardware address.
4.  **Inspect MAC Data:** Double-clicked the first packet and expanded **Ethernet II** to verify the MAC address filter worked.
5.  **Clear Filter:** Clicked the 'X Clear display filter' icon.

---

## 4. Task 4 & 5: Application Layer Deep Dive

This final section covered how to analyze application-specific protocols and search the raw data.

1.  **Filter for DNS:** Entered the filter `udp.port == 53` to isolate all DNS lookups.
2.  **Inspect DNS Query:** Double-clicked a DNS packet and expanded the **Domain Name System (query)** subtree to find the website name requested (`opensource.google.com`).
3.  **Filter for HTTP:** Entered the filter `tcp.port == 80` to find unencrypted web traffic.
4.  **Search the Data Payload:** Entered the content search filter `tcp contains "curl"` to find packets that included that specific text string in the data section.

---

* **Author:** Joan

---
