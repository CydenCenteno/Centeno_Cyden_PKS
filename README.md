# Personal Knowledge System (PKS)

**Author:** Centeno, Cyden
**Course:** Midterm Project
**Format:** Markdown notes, local images only (no external dependencies)

Curated reference notes. Not full coverage — only concepts worth keeping.

## How to Use

1. Start here. Pick subject.
2. Each subject folder = numbered notes, read in order.
3. Each note ends with **Gotchas** / **Quick recall**.
4. Unknown term → [00_glossary.md](00_glossary.md).

## Index

| # | Subject | Notes |
|---|---------|-------|
| 01 | Cybersecurity | [CIA & basics](01_cybersecurity/01_cia_and_basics.md) · [Threats & attacks](01_cybersecurity/02_threats_and_attacks.md) · [Defenses](01_cybersecurity/03_defenses.md) |
| 02 | Fundamentals of Programming | [Core concepts](02_programming_fundamentals/01_core_concepts.md) · [Java reference](02_programming_fundamentals/02_java_reference.md) |
| 03 | Front End | [HTML & CSS](03_front_end/01_html_css.md) · [JavaScript & DOM](03_front_end/02_javascript_dom.md) |
| 04 | Back End | [HTTP & REST](04_back_end/01_http_and_rest.md) · [Databases & SQL](04_back_end/02_databases_sql.md) |
| 05 | Basic IT Fundamentals | [Hardware, software, OS](05_it_fundamentals/01_hardware_software_os.md) · [Networking](05_it_fundamentals/02_networking_basics.md) |
| 06 | SIA (System Integration & Architecture) | [Architecture patterns](06_sia/01_architecture_patterns.md) · [Integration](06_sia/02_integration.md) |
| 07 | IT Elective | [Elective notes](07_it_elective/01_elective_notes.md) |
| — | Glossary | [00_glossary.md](00_glossary.md) |

## Folder Structure

```
Centeno_Cyden_PKS/
├── README.md
├── 00_glossary.md
├── assets/                  <- all images (local SVG)
├── 01_cybersecurity/
├── 02_programming_fundamentals/
├── 03_front_end/
├── 04_back_end/
├── 05_it_fundamentals/
├── 06_sia/
└── 07_it_elective/
```

## Cross-Subject Map

- Cybersecurity ↔ Back End: SQL injection, password hashing, sessions/JWT.
- Cybersecurity ↔ Front End: XSS, CSRF, input validation.
- Back End ↔ SIA: REST APIs = main integration method.
- Basic IT ↔ Cybersecurity: networking ports/protocols = attack surface.
- Programming ↔ everything: OOP, error handling, clean functions.

![Client-server request flow](assets/client-server-flow.svg)
