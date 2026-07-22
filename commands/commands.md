# Commands Used

## Ubuntu

```bash
sudo apt update
sudo apt upgrade -y
```

```bash
ip a
```

```bash
sudo apt install wireshark -y
```

```bash
sudo wireshark
```

---

## Kali

```bash
sudo apt update
sudo apt upgrade -y
```

```bash
sudo apt install dnsutils -y
```

```bash
nslookup bitpluss.com
```

```bash
dig bitpluss.com
```

```bash
nslookup github.com
```

```bash
nslookup ubuntu.com
```

```bash
for domain in google.com github.com microsoft.com openai.com ubuntu.com kali.org
do
    nslookup $domain
done
```

```bash
nslookup fake-domain-12345.local
```
