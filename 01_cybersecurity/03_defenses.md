# Cybersecurity — Defenses

## Cryptography

| Concept | Key use | Example | Notes |
|---------|---------|---------|-------|
| Symmetric | One shared key | AES | Fast; key distribution problem |
| Asymmetric | Public + private key pair | RSA, ECC | Slower; solves key exchange |
| Hashing | No key, one-way | SHA-256, bcrypt | Integrity, password storage |
| Digital signature | Sign with private, verify with public | RSA/ECDSA | Integrity + authenticity + non-repudiation |

- **TLS/HTTPS** — asymmetric exchange sets up symmetric session key.
- Encryption is reversible. Hashing is not.

## Password Storage

- Never store plaintext. Never use plain MD5/SHA-1.
- Use slow, salted hash: **bcrypt**, **Argon2**, **PBKDF2**.
- **Salt** = random per-user value; defeats rainbow tables.

## Access Control

- **MFA** — two or more factor types.
- **RBAC** — permissions by role.
- **Least privilege** — default deny.

## Network Defenses

- **Firewall** — filters traffic by rules.
- **IDS** detects; **IPS** detects and blocks.
- **VPN** — encrypted tunnel.
- **Network segmentation / DMZ** — isolate public-facing systems.

## Operational Hygiene

- Patch and update promptly.
- Backups: **3-2-1** — 3 copies, 2 media types, 1 offsite. Test restores.
- Logging and monitoring.
- Security awareness training.

## Secure Coding Checklist

1. Validate and sanitize all input (server-side).
2. Use parameterized queries.
3. Encode output.
4. Hash passwords with bcrypt/Argon2.
5. Enforce HTTPS.
6. Hide detailed errors from users.
7. Keep dependencies updated.
8. Store secrets in environment variables, not source code.

Java prepared statement:

```java
String sql = "SELECT id FROM users WHERE email = ?";
try (PreparedStatement ps = conn.prepareStatement(sql)) {
    ps.setString(1, email);          // value bound, never concatenated
    try (ResultSet rs = ps.executeQuery()) {
        // handle rows
    }
}
```

## OWASP Top 10 (themes)

Broken access control · Cryptographic failures · Injection · Insecure design · Security misconfiguration · Vulnerable components · Authentication failures · Integrity failures · Logging failures · SSRF.

## Incident Response Phases

Preparation → Identification → Containment → Eradication → Recovery → Lessons learned.

## Gotchas

- Backup that is never tested = no backup.
- Encryption protects confidentiality, not integrity by itself.
- Never hard-code credentials or commit secrets to Git.
