DNS Traffic Investigation Report
Author

Mubarak Bashr

Project Overview

This project demonstrates a DNS Traffic Investigation performed in an isolated virtual laboratory using Kali Linux, Ubuntu Linux, and Wireshark. The objective was to generate DNS traffic, capture packets, analyze DNS communication, identify failed lookups, and document the investigation process.

Objectives
Generate legitimate DNS traffic.
Capture DNS packets using Wireshark.
Analyze DNS queries and responses.
Investigate A and AAAA record lookups.
Identify NXDOMAIN responses.
Review protocol statistics.
Analyze endpoints and conversations.
Practice Wireshark display filters.
Lab Environment
Component	Details
Monitoring Machine	Ubuntu Linux
Client Machine	Kali Linux
Packet Analyzer	Wireshark 4.6.4
DNS Tools	nslookup, dig
Network	VMware Virtual Network
Interface	ens33
Investigation Procedure
1. System Preparation

Both Ubuntu and Kali Linux machines were updated before beginning the investigation.

Ubuntu detected one upgradeable package that remained pending because of Ubuntu's package phasing mechanism.

Kali Linux was already fully updated.

2. Network Verification

The network interface was verified using the following command:

ip a

The active interface was ens33 with the IPv4 address:

192.168.81.129/24
3. DNS Traffic Generation

DNS traffic was generated using several domains including:

bitpluss.com
github.com
ubuntu.com
google.com
microsoft.com
openai.com
kali.org

The following tools were used:

nslookup
dig
4. Simulated Failed DNS Query

A fake domain was intentionally queried:

fake-domain-12345.local

The DNS server returned:

NXDOMAIN

This simulated an unsuccessful DNS lookup for investigation purposes.

5. Packet Capture

Wireshark was launched on Ubuntu.

The ens33 interface was selected.

Traffic was captured while DNS requests were generated from Kali Linux.

The capture was saved as:

dns-traffic-investigation.pcapng
Traffic Analysis
Capture Statistics
Item	Value
Total Packets	2212
Capture Duration	7 Minutes 46 Seconds
Average Packets/sec	4.7
Average Data Rate	35 KB/sec
Protocol Hierarchy

Analysis showed:

IPv4 represented approximately 97.8% of packets.
TCP generated the majority of traffic.
TLS transferred the largest amount of data.
DNS represented approximately 2.4% of captured packets.
UDP was mainly used for DNS and NTP communication.
Endpoint Analysis

The capture identified multiple IPv4 endpoints.

The Ubuntu monitoring machine generated most of the traffic.

The external server 151.101.210.49 exchanged approximately 2 MB of traffic during the capture.

Conversation Analysis

Wireshark Conversations identified twelve IPv4 conversations.

The largest communication occurred between:

192.168.81.129
↓

151.101.210.49

Additional DNS and NTP conversations were also observed.

Wireshark Filters Used
Filter	Purpose
dns	Show all DNS packets
dns.flags.response == 0	DNS queries only
dns.flags.response == 1	DNS responses only
dns.qry.type == 1	A records
dns.qry.type == 28	AAAA records
udp	UDP traffic
udp.port == 53	DNS over UDP
dns.flags.rcode != 0	DNS errors
Key Findings
DNS communication operated normally using UDP port 53.
Multiple legitimate domains resolved successfully.
IPv4 and IPv6 addresses were returned correctly.
One intentionally generated fake domain produced an NXDOMAIN response.
No suspicious DNS tunneling or abnormal DNS behavior was detected.
Evidence
Capture File
dns-traffic-investigation.pcapng
Failed DNS Query
fake-domain-12345.local
Response
NXDOMAIN
Query Packet
2189
Response Packet
2190
Conclusion

The DNS Traffic Investigation successfully demonstrated how DNS requests and responses can be generated, captured, and analyzed using Wireshark. The project verified normal DNS communication patterns while documenting a controlled NXDOMAIN event. Protocol hierarchy, endpoint statistics, conversation analysis, and Wireshark filtering techniques provided valuable insight into DNS traffic behavior within a secure laboratory environment.
