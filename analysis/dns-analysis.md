# DNS Analysis

## DNS Server

192.168.81.2

---

## Successful Queries

- bitpluss.com
- github.com
- ubuntu.com
- google.com
- microsoft.com
- openai.com
- kali.org

---

## Failed Query

fake-domain-12345.local

Result:

NXDOMAIN

---

## Record Types

### A Record

IPv4 Address Resolution

### AAAA Record

IPv6 Address Resolution

---

## Observations

DNS communication was performed over UDP port 53.

Both IPv4 and IPv6 addresses were successfully returned for several domains.

One intentionally generated fake domain produced an NXDOMAIN response.
