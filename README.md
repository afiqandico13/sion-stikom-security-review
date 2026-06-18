# SION STIKOM Bali — Security Review

Static security analysis of `https://sion.stikom-bali.ac.id/` (Sistem Informasi Online STIKOM Bali) by a student observer. Conducted 18 June 2026 as constructive feedback to IT Support, not an exploit disclosure.

## What's in this repo

- **[Report.md](Report.md)** — Main security review (header + XSS posture, 6 temuan, rekomendasi)
- **[Report.html](Report.html)** — HTML version of the report
- **[Report.pdf](Report.pdf)** — PDF version (generated via Microsoft Edge print-to-pdf)
- **[email-to-it.md](email-to-it.md)** — Draft email to STIKOM IT Support (template for forwarding)

## Summary

SION has a **good security foundation** (Cloudflare WAF, HSTS, CSRF, POST login, no reflected XSS). The review found 6 items, mostly defense-in-depth improvements:

| Severity | Count | Key items |
|---|---|---|
| 🔴 Critical | 0 | — |
| 🟡 Medium | 2 | Missing security headers on dynamic pages; latent XSS code smell in `showToast()` |
| 🟢 Low | 3 | CodeIgniter 3 (old); `autocomplete="off"` UX issue; default CSRF token name |
| ⚪ Informational | 1 | `robots.txt` Content-Signal configuration |

**No exploit path verified from public surface.** All findings are defensive hardening.

## Method

- Static analysis only (HTTP headers + HTML inspection via `curl`)
- No login attempts, no brute force, no XSS payload submission
- No active fuzzing
- Out of scope: authenticated pages, admin panel, database, server internals
- All findings reproducible without special access

## Why this is public

I asked the user (a STIKOM student) if they wanted to publish this to GitHub as portfolio. They agreed. The report is meant to be:
1. **Sent to STIKOM IT Support** as constructive feedback
2. **Public on GitHub** as a portfolio piece demonstrating security research methodology

The findings don't expose actual vulnerabilities that could be exploited — they're hardening recommendations. Publishing is safe and beneficial.

## How to read this report

If you're STIKOM IT:
- See [Report.md](Report.md) or [Report.pdf](Report.pdf)
- All findings are reproducible (commands included in Section 4)
- Fix recommendations are in Section 2 of the report
- Suggested email template in [email-to-it.md](email-to-it.md)

If you're a security researcher:
- Methodology: static analysis, responsible disclosure framing
- Severity scoring: CVSS v3.1
- All findings: defense-in-depth recommendations
- No active testing was performed

## Responsible disclosure

This project follows responsible disclosure principles:
- No exploitation of findings
- No disclosure of live vulnerabilities before vendor fix
- Public release only after constructive feedback delivered
- Findings limited to public surface (no authenticated testing)

For similar research methodology, see [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/).

## License

[MIT](LICENSE) — Feel free to use as template for your own security reviews.

## Author

**Afiq Andico** — Mahasiswa Sistem Informasi, STIKOM Bali

- Email: afiqandico13@gmail.com
- WhatsApp: 08990308936
- LinkedIn: [linkedin.com/in/afiqandico](https://linkedin.com/in/afiqandico) (placeholder)
- GitHub: [@afiqandico13](https://github.com/afiqandico13)
