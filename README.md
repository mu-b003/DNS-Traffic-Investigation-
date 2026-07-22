# DNS Traffic Investigation

## Overview

This project demonstrates a DNS Traffic Investigation performed inside an isolated virtual laboratory using Kali Linux, Ubuntu, and Wireshark. The objective was to generate legitimate DNS traffic, capture it, analyze DNS queries and responses, identify failed lookups (NXDOMAIN), and understand DNS communication patterns.

---

## Objectives

- Capture DNS traffic using Wireshark.
- Analyze DNS queries and responses.
- Investigate A and AAAA records.
- Identify failed DNS requests (NXDOMAIN).
- Analyze protocol distribution.
- Review network conversations and endpoints.
- Practice Wireshark filtering techniques.

---

## Lab Environment

| Component | Details |
|-----------|---------|
| Attacker Machine | Kali Linux |
| Monitoring Machine | Ubuntu Linux |
| Packet Analyzer | Wireshark 4.6.4 |
| DNS Utility | nslookup |
| DNS Utility | dig |
| Network | VMware Virtual Network |
| Interface | ens33 |

---

## Tools Used

- Wireshark
- nslookup
- dig
- Ubuntu Linux
- Kali Linux

---

## Investigation Steps

1. Update both virtual machines.
2. Verify network configuration.
3. Install DNS utilities.
4. Generate DNS traffic.
5. Capture packets using Wireshark.
6. Save the capture file.
7. Analyze the captured traffic.
8. Apply Wireshark filters.
9. Identify normal and failed DNS requests.
10. Document findings.

---

## Wireshark Filters Used

| Filter | Purpose |
|---------|---------|
| dns | Display all DNS packets |
| dns.flags.response==0 | DNS Queries |
| dns.flags.response==1 | DNS Responses |
| dns.qry.type==1 | A Records |
| dns.qry.type==28 | AAAA Records |
| udp | UDP Traffic |
| udp.port==53 | DNS Traffic |
| dns.flags.rcode!=0 | DNS Errors |

---

## Findings

- DNS traffic was successfully generated.
- Multiple legitimate domains resolved correctly.
- DNS communication used UDP port 53.
- One intentionally generated fake domain returned NXDOMAIN.
- DNS packets represented approximately 2.4% of total captured traffic.

---

## Key Evidence

- Total Packets: 2212
- DNS Packets: 52
- DNS Queries: 30
- DNS Responses: 26
- Failed Queries: 1
- Failed Domain: fake-domain-12345.local

---

## Conclusion

The investigation successfully demonstrated how DNS requests and responses can be captured and analyzed using Wireshark. The generated NXDOMAIN response confirmed the ability to identify failed DNS lookups, while protocol statistics and endpoint analysis provided additional insight into normal network behavior.

---

## Author

Mubarak Bashr
