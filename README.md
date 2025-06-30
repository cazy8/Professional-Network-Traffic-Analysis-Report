# Professional-Network-Traffic-Analysis-Report
Network Traffic Analysis Report - Task 5
Overview
This repository contains the analysis report and findings for Task 5: Capture and Analyze Network Traffic Using Wireshark. The task involved capturing live network packets, identifying basic protocols, and analyzing traffic patterns using Wireshark.

Key Findings
TCP Dominance: 85% of captured traffic consisted of TCP ACK packets maintaining connections

DNS Misconfiguration: Reverse DNS lookup failed due to missing PTR records

TLS Encryption: Secure TLS 1.2 communication detected

Network Health Issues: TCP duplicate ACKs suggest potential packet loss

Traffic Distribution: Connections to content delivery networks (Akamai, Google)

Protocol Distribution
Diagram
Code
pie
    title Protocol Distribution
    "TCP" : 85
    "DNS" : 8
    "TLS" : 7
Repository Structure
text
📂 ElevateLabs-Task5-Network-Analysis/
├── 📄 README.md                   # This documentation
├── 📄 Network_Analysis_Report.pdf # Complete analysis report
├── 📄 packet_capture.pcap         # Original packet capture file
├── 📄 analysis_summary.txt        # Key findings summary
└── 📄 mitigation_commands.sh      # Recommended fixes
How to Use This Repository
1. Review the Analysis Report
Open Network_Analysis_Report.pdf for:

Detailed protocol breakdown

Technical observations

Security assessment

Complete packet capture table

2. Analyze the PCAP File
Install Wireshark:

bash
# Linux
sudo apt update && sudo apt install wireshark

# Windows: Download from https://www.wireshark.org/download.html
Open the capture file:

bash
wireshark packet_capture.pcap
Apply key filters:

python
tcp.analysis.duplicate_ack  # Identify retransmissions
dns                         # DNS queries and responses
tls                         # TLS encrypted traffic
ip.addr == 192.168.26.130   # Filter by source IP
3. Implement Recommendations
Execute mitigation commands:

bash
# Run network optimization checks
bash mitigation_commands.sh --check

# Apply DNS configuration fix
bash mitigation_commands.sh --dns-fix
Critical Observations
TCP Retransmissions: 10 duplicate ACKs indicating network issues

bash
Packets 17-26: [TCP Dup ACK] flags
DNS Configuration Error:

bash
Query: 130.26.168.192.in-addr.arpa
Response: No such name (NXDOMAIN)
Encrypted Traffic:

bash
Packets 13,15: TLSv1.2 Application Data to 34.36.137.203:443
Recommendations
Network Optimization:

bash
# Check packet loss
ping -c 100 8.8.8.8 | grep loss

# Monitor interface errors
ip -s link show wlan0
DNS Configuration Fix:

bash
# Add reverse DNS record
$ORIGIN 26.168.192.in-addr.arpa.
130   PTR   hostname.example.com.
Security Enhancements:

Upgrade HTTP connections to HTTPS

Implement TLS 1.3 prioritization

Configure network monitoring
