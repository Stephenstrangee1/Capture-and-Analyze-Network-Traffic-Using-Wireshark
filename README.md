# Cyber Security Internship Task 5: Capture and Analyze Network Traffic Using Wireshark

## Introduction
This repository documents my completion of Task 5 from the Elevate Labs Cyber Security Internship program. The objective was to capture live network packets using Wireshark, identify basic protocols and traffic types, and generate a report. This exercise provided hands-on experience with packet capture, protocol analysis, and network troubleshooting.

Key learnings: Wireshark allows visibility into network traffic at the packet level, helping identify protocols like DNS for name resolution, ICMP for ping diagnostics, and TLS for secure communications. I captured traffic on a Kali Linux VM (interface eth0) by pinging, querying DNS, and curling google.com to generate diverse packets.

## Tools Used
- **Wireshark**: Free packet analyzer (installed on Kali Linux).
- **Operating System**: Kali Linux (running in VMware).
- **Terminal Commands**: Used to generate traffic (e.g., ping, curl, nslookup).
- No additional paid tools required.

## Steps Followed
I followed the task's Hints/Mini Guide step-by-step:

1. **Install Wireshark**: Already installed on Kali Linux; verified with `wireshark --version`.

2. **Start Capturing on Active Network Interface**: Opened Wireshark, selected eth0 (active interface, IP: 192.168.xxx.xxx from `ip addr show`), and started capture.

3. **Browse a Website or Ping a Server to Generate Traffic**: Ran commands to generate traffic:
   - `ping -c 5 google.com` for ICMP.
   - `nslookup google.com` for DNS.
   - `curl google.com` for HTTP/TLS (redirects to HTTPS).

4. **Stop Capture After a Minute**: Captured for ~1 minute, then stopped.

5. **Filter Captured Packets by Protocol**: Applied filters:
   - `tls` for TLS packets.
   - `icmp` for ICMP packets.
   - `dns` for DNS packets.

6. **Identify at Least 3 Different Protocols**: Identified:
   - **TLS**: Secure communication (e.g., Client Hello to google.com on port 443).
   - **ICMP**: Ping requests/replies (e.g., Echo request/reply with TTL=128).
   - **DNS**: Queries/responses (e.g., A/AAAA records for google.com).

7. **Export the Capture as a .pcap File**: Exported as traffic_capture.pcap

8. **Summarize Your Findings and Packet Details**:
   - **Total Packets**: ~654 (from ICMP screenshot), but varied per capture.
   - **TLS Findings**: Handshake packets (Client Hello, Server Hello, Change Cipher Spec). Source: 192.168.xxx.xxx, Destination: 142.251.xxx.xxx (Google IP). Protocol: TLSv1.3.
   - **ICMP Findings**: 5 Echo requests/replies to google.com (142.250.183.238). Times: 50.9ms to 190ms. Useful for testing connectivity.
   - **DNS Findings**: Standard queries for google.com A/AAAA records. Responses included IPs like 142.250.193.110 and 2404:6800:4007:815::200e.
   - Traffic Generation Log: See Generate Traffic Report.txt for full commands and outputs.
   - Screenshots:
     - tls-screenshot.png (TLS packets from curl).
     - icmp-screenshot.png (ICMP from ping).
     - dns-screenshot.png (DNS from nslookup/curl).

## Packet Capture Files and Reports
- **Traffic Generation Log**: Generate Traffic Report.txt – Terminal commands and outputs used to create traffic.
- **Task Description**: task 5.pdf – The original PDF for reference.


## Conclusion
This task enhanced my packet analysis skills, showing how protocols like DNS, ICMP, and TLS work in real traffic. I captured and filtered packets successfully, identifying 3+ protocols. Future improvements: Capture encrypted vs. unencrypted traffic or use tshark for CLI analysis.

For questions or feedback, contact me at stephenbrave@gmail.com. Task description: task 5.pdf.
