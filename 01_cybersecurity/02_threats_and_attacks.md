# Cybersecurity — Threats & Attacks

## Malware Types

| Type | Behavior |
|------|----------|
| Virus | Attaches to files, needs user action to spread |
| Worm | Self-replicates across networks |
| Trojan | Disguised as legitimate software |
| Ransomware | Encrypts data, demands payment |
| Spyware | Secretly collects information |
| Keylogger | Records keystrokes |
| Rootkit | Hides deep in OS, persistent access |
| Botnet | Network of infected machines under attacker control |

## Social Engineering

- **Phishing** — fake email/message to steal credentials. Variants: spear phishing (targeted), whaling (executives), smishing (SMS), vishing (voice).
- **Pretexting** — invented scenario to extract info.
- **Baiting** — infected USB / tempting download.
- **Tailgating** — following authorized person into restricted area.

Red flags: urgency, mismatched sender/domain, unexpected attachment, request for credentials.

## Network Attacks

- **DoS / DDoS** — flood target, break availability.
- **MITM** — attacker intercepts/alters communication.
- **Packet sniffing** — capture unencrypted traffic.
- **Spoofing** — fake IP/MAC/DNS identity.
- **Port scanning** — recon for open services.

## Password Attacks

- Brute force · Dictionary · Credential stuffing (reused leaked passwords) · Rainbow table (defeated by salting).

## Web Application Attacks

| Attack | How | Prevent |
|--------|-----|---------|
| SQL injection | Input changes SQL query | Prepared statements, input validation |
| XSS | Injected script runs in victim browser | Output encoding, CSP, sanitize input |
| CSRF | Forged request using victim's session | CSRF tokens, SameSite cookies |
| Broken authentication | Weak login/session handling | MFA, secure sessions, lockout |
| Insecure direct object reference | Change ID in URL to see others' data | Server-side authorization checks |

SQLi example (vulnerable):

```sql
-- input: ' OR '1'='1
SELECT * FROM users WHERE name = '' OR '1'='1';  -- returns all rows
```

## Gotchas

- Insider threats exist — not all attackers are external.
- Zero-day = no patch available yet.
- Client-side validation is bypassable. Always validate server-side.
