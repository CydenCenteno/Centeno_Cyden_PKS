# Basic IT Fundamentals — Networking Basics

## Network Types

LAN (local) · WAN (wide) · MAN (city) · PAN (personal) · WLAN (wireless LAN).

## Devices

| Device | Layer | Job |
|--------|-------|-----|
| Hub | 1 | Broadcasts to all ports (obsolete) |
| Switch | 2 | Forwards by MAC address |
| Router | 3 | Connects networks, forwards by IP |
| Firewall | 3–7 | Filters traffic |
| Access point | 2 | Wireless connectivity |

## OSI vs TCP/IP

| OSI layer | TCP/IP layer | Examples |
|-----------|--------------|----------|
| 7 Application | Application | HTTP, DNS, SMTP, FTP |
| 6 Presentation | ↑ | Encryption, encoding |
| 5 Session | ↑ | Session control |
| 4 Transport | Transport | TCP, UDP |
| 3 Network | Internet | IP, ICMP |
| 2 Data Link | Network Access | Ethernet, Wi-Fi, MAC |
| 1 Physical | ↑ | Cables, signals |

Mnemonic (top→bottom): **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing.

## IP Addressing

- IPv4: 32-bit, e.g. `192.168.1.10`. IPv6: 128-bit.
- Private ranges: `10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`.
- Subnet mask `255.255.255.0` = `/24` → 254 usable hosts.
- Usable hosts = 2^(host bits) − 2 (minus network and broadcast).
- Default gateway = router address leaving the LAN.

## Essential Protocols

| Protocol | Port | Purpose |
|----------|------|---------|
| HTTP | 80 | Web |
| HTTPS | 443 | Encrypted web |
| FTP | 21 | File transfer |
| SSH | 22 | Secure remote shell |
| SMTP | 25 | Send email |
| DNS | 53 | Name resolution |
| DHCP | 67/68 | Auto IP assignment |
| RDP | 3389 | Remote desktop |
| MySQL | 3306 | Database |

## TCP vs UDP

- **TCP** — reliable, ordered, connection (3-way handshake: SYN, SYN-ACK, ACK). Web, email.
- **UDP** — fast, no guarantee. Streaming, gaming, DNS queries.

## DNS & DHCP

- **DNS** — `example.com` → IP address.
- **DHCP** — server automatically assigns IP, mask, gateway, DNS.
- **NAT** — many private IPs share one public IP.

## Diagnostic Commands

```bash
ping 8.8.8.8          # reachability
ipconfig / ifconfig   # local IP config (ip a on Linux)
nslookup example.com  # DNS lookup
tracert / traceroute  # path to destination
netstat -an           # open connections/ports
```

## Gotchas

- Ping by IP works but name fails → DNS problem.
- Telnet/FTP/HTTP send plaintext — use SSH/SFTP/HTTPS.
- Open ports = attack surface; close unused ones.
- `127.0.0.1` = localhost (own machine).
