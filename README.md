# Wireshark-packet-protocol-analysis
# 📊 Network Traffic Capture & Protocol Analysis (Wireshark)

## 🎯 Objective
To capture live network traffic using Wireshark, filter protocols, and analyze at least three types of common network interactions: **DNS**, **HTTP**, and **ICMP**.

## 🛠️ Tools Used
- **Wireshark** – for capturing and analyzing packet-level network traffic.

## 📥 Methodology
1. Launched Wireshark and selected the active network interface (`192.168.220.236`).
2. Initiated traffic:
   - Browsed to `www.jio.com` to generate **DNS** and **HTTP** packets.
   - Used the `ping` command to `8.8.8.8` to generate **ICMP** traffic.
3. Stopped capture after ~60 seconds and saved the file as `capture.pcap`.
4. Filtered and analyzed individual protocol layers using display filters:  
   `dns`, `icmp`, `http`.

## 🔍 Protocols Identified & Analyzed

### 1. 🌐 DNS (Domain Name System)
- **Function:** Resolves domain names to IP addresses.
- **Captured Packets:** 963, 964 (Queries); 965 (Response)
- **Flow Summary:**
  - A record query for `www.jio.com`
  - Response with resolved IP `49.40.8.179`
- **Notable:** Duplicate query indicated potential retry behavior.

### 2. 📶 ICMP (Internet Control Message Protocol)
- **Function:** Diagnostic protocol used for connectivity checks.
- **Captured Packets:** 4951 ↔ 4956, 4981 ↔ 4980, 4993 ↔ 4997, 5044 ↔ 5053
- **Flow Summary:**
  - Echo requests sent to `8.8.8.8`
  - Replies confirmed successful round-trip communication.
- **Notable:** No packet loss, clean round-trip pairings.

### 3. 🌍 HTTP (Hypertext Transfer Protocol)
- **Function:** Facilitates web requests over TCP.
- **Captured Packets:** 1074 (GET request), 1083 (302 redirect)
- **Flow Summary:**
  - Client requested `GET /`
  - Server responded with a 302 redirect
- **Notable:** Communication occurred in plaintext (HTTP, not HTTPS).
