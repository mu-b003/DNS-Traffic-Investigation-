DNS Traffic Investigation Report

Author: Mubarak Bashr
Project: DNS Traffic Investigation
Environment: Kali Linux, Ubuntu Linux, Wireshark
Date: July 2026

Abstract

This report documents a DNS Traffic Investigation performed in an isolated virtual laboratory. The objective was to generate DNS traffic, capture network packets using Wireshark, analyze DNS queries and responses, identify failed lookups (NXDOMAIN), and understand DNS communication behavior. The investigation demonstrates practical DNS analysis techniques commonly used in SOC environments and network forensic investigations.

Objectives
Capture DNS traffic using Wireshark.
Analyze DNS queries and responses.
Examine A and AAAA DNS records.
Investigate DNS protocol behavior.
Identify unsuccessful DNS lookups (NXDOMAIN).
Practice packet filtering and protocol analysis.
Lab Environment
Component	Details
Monitoring Machine	Ubuntu Linux
Client Machine	Kali Linux
Packet Analyzer	Wireshark 4.6.4
DNS Utilities	nslookup, dig
Network Interface	ens33
Network Type	VMware Virtual Network
Investigation Procedure

The Ubuntu and Kali Linux systems were updated before starting the investigation. The network configuration was verified to ensure proper connectivity between both virtual machines.

DNS utilities were installed on Kali Linux, and several DNS queries were generated using nslookup and dig. Domains including bitpluss.com, github.com, ubuntu.com, google.com, microsoft.com, openai.com, and kali.org were queried successfully.

A fake domain (fake-domain-12345.local) was queried intentionally to generate an NXDOMAIN response for analysis.

Wireshark captured all traffic on the ens33 interface while DNS requests were generated.

Traffic Statistics
Item	Value
Total Packets	2212
Capture Duration	7 Minutes 46 Seconds
DNS Packets	52
DNS Queries	30
DNS Responses	26
Failed DNS Queries	1
UDP Packets	157
Protocol Analysis

Protocol hierarchy analysis showed that IPv4 represented approximately 97.8% of captured packets.

TCP generated most of the network traffic, while TLS accounted for the majority of transferred data. DNS traffic represented approximately 2.4% of all captured packets and operated over UDP port 53. NTP and ARP traffic were also observed during the capture.

Endpoint Analysis

Endpoint analysis identified thirteen IPv4 endpoints. The Ubuntu monitoring machine generated the majority of network traffic. Communication with external servers occurred normally during DNS resolution and encrypted web connections.

Conversation Analysis

Conversation statistics displayed twelve IPv4 conversations.

The largest communication occurred between the Ubuntu machine and an external server, while smaller conversations included DNS and NTP traffic.

No suspicious communication patterns were identified.

Wireshark Filters Used
Filter	Description
dns	Display all DNS packets
dns.flags.response == 0	DNS queries only
dns.flags.response == 1	DNS responses only
dns.qry.type == 1	A record queries
dns.qry.type == 28	AAAA record queries
udp	Display all UDP packets
udp.port == 53	DNS traffic over UDP
dns.flags.rcode != 0	DNS responses containing errors
Findings
DNS traffic was successfully captured.
All legitimate domains resolved correctly.
DNS communication occurred through UDP port 53.
IPv4 and IPv6 records were successfully returned.
One intentionally generated fake domain produced an NXDOMAIN response.
No abnormal DNS behavior or DNS tunneling was detected.
Key Evidence
Evidence	Value
Capture File	dns-traffic-investigation.pcapng
Failed Domain	fake-domain-12345.local
Error Type	NXDOMAIN
Query Packet	2189
Response Packet	2190
Conclusion

The DNS Traffic Investigation successfully demonstrated how DNS traffic can be generated, captured, filtered, and analyzed using Wireshark. The investigation confirmed normal DNS communication patterns and documented a controlled NXDOMAIN event for forensic analysis. This project provided practical experience in DNS monitoring, packet analysis, and Wireshark filtering techniques commonly used in Security Operations Center (SOC) environments.
