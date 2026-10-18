# Basic IT Fundamentals — Hardware, Software, OS

## Computer Components

| Component | Job |
|-----------|-----|
| CPU | Executes instructions (cores, clock speed, cache) |
| RAM | Volatile working memory; lost on power off |
| Storage | Persistent: HDD (mechanical, cheap), SSD (flash, fast) |
| Motherboard | Connects all components |
| GPU | Parallel graphics/compute |
| PSU | Converts AC to DC power |

Input: keyboard, mouse, scanner. Output: monitor, printer, speakers.

Memory hierarchy (fast/small → slow/large): registers → cache → RAM → SSD/HDD.

## Software Types

- **System software** — OS, drivers, utilities.
- **Application software** — word processors, browsers, games.
- **Firmware** — software embedded in hardware (BIOS/UEFI).
- Licenses: proprietary, open source, freeware, shareware.

## Operating System Functions

1. Process management (scheduling)
2. Memory management
3. File system management
4. Device management (drivers)
5. User interface (CLI/GUI)
6. Security and access control

Common OS: Windows, macOS, Linux, Android, iOS.

## File Systems

NTFS (Windows) · ext4 (Linux) · APFS (macOS) · FAT32/exFAT (portable drives).

## Number Systems

| System | Base | Digits |
|--------|------|--------|
| Binary | 2 | 0–1 |
| Octal | 8 | 0–7 |
| Decimal | 10 | 0–9 |
| Hexadecimal | 16 | 0–9, A–F |

Binary → decimal: `1011₂ = 8 + 0 + 2 + 1 = 11`.
Decimal → binary: divide by 2, read remainders bottom-up.
Units: 1 byte = 8 bits; 1 KB = 1024 bytes (binary convention).

## Useful Commands

```bash
ls        # list files (Linux/macOS)      dir (Windows)
cd path   # change directory
pwd       # print working directory
mkdir x   # make directory
cp a b    # copy
mv a b    # move/rename
rm x      # delete (no recycle bin!)
```

## Troubleshooting Method

Identify problem → establish theory → test theory → plan fix → implement → verify → document.

## Gotchas

- RAM ≠ storage.
- Clock speed alone does not decide CPU performance (cores, architecture, cache matter).
- 32-bit OS addresses ~4 GB RAM max.
- `rm` and `del` are permanent — verify path first.
