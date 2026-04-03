<div align="center">

# 📖 Usage Guide

**Shadow Recon — Complete usage reference**

[![Back to README](https://img.shields.io/badge/←%20Back%20to-README-blueviolet?style=for-the-badge)](README.md)

</div>

---

## 📑 Table of Contents

- [🚀 Running the Tool](#-running-the-tool)
- [🕰️ Wayback URLs Option](#️-wayback-urls-option)
- [📁 Output Breakdown](#-output-breakdown)
- [✅ Best Practices](#-best-practices)
- [💡 Tips](#-tips)

---

## 🚀 Running the Tool

### Single Domain

```bash
./recon.sh example.com
```

### Multiple Domains

```bash
./recon.sh domains.txt
```

> [!NOTE]
> For multiple domains, provide a plain text file with one domain per line.

---

## 🕰️ Wayback URLs Option

During execution, you'll be prompted:

```
Do you want to run waybackurls? (y/n)
```

| Choice | Result |
|--------|--------|
| `y` | Collects historical URLs from the Wayback Machine archive |
| `n` | Skips this step and continues with live data only |

> [!TIP]
> Running Wayback URLs can significantly increase discovered endpoints — recommended for thorough assessments.

---

## 📁 Output Breakdown

All results are saved under `recon_results/`:

```
recon_results/
│
├── 📂 subdomains/
│   ├── all_unique_subdomains.txt   ← Combined raw subdomain list
│   └── subdomains.txt              ← Cleaned & deduplicated list
│
├── 📂 urls/
│   ├── extracted.txt               ← Live extracted endpoints
│   └── wayback.txt                 ← Historical URLs (if enabled)
│
├── 📂 cors/
│   └── potential.txt               ← Potentially misconfigured domains
│
├── 📂 fff_output/
│   └── *.txt                       ← Raw HTTP responses
│
└── 📂 juicy/
    ├── api-keys.txt                 ← Exposed API credentials
    ├── jwt.txt                      ← JWT token leaks
    ├── sqli.txt                     ← SQL injection vectors
    ├── lfi.txt                      ← Local file inclusion patterns
    └── rce.txt                      ← Remote code execution indicators
```

### 🔍 Key Files at a Glance

| File | Description |
|------|-------------|
| `subdomains/subdomains.txt` | Final clean subdomain list |
| `subdomains/httprobe.txt` | Verified live & active hosts |
| `cors/potential.txt` | CORS misconfiguration candidates |
| `juicy/` | All vulnerability pattern matches |

---

## ✅ Best Practices

> [!IMPORTANT]
> Always ensure you have **explicit written permission** before running recon on any target.

- 🎯 **Scope it** — only target authorized domains
- 🖥️ **Use a VPS** — better bandwidth, IP diversity, and performance
- 🔗 **Chain your tools** — combine Shadow Recon output with:

| Tool | Use Case |
|------|----------|
| [Nuclei](https://github.com/projectdiscovery/nuclei) | Template-based vulnerability scanning |
| [ffuf](https://github.com/ffuf/ffuf) | Directory & parameter fuzzing |
| [Burp Suite](https://portswigger.net/burp) | Manual request inspection & testing |

---

## 💡 Tips

> [!TIP]
> A few habits that will level up your recon workflow:

- 🔄 **Keep tools updated** — run `go install` updates regularly for Subfinder, httpx, etc.
- ⏰ **Run periodically** — new subdomains and assets appear over time; schedule recon jobs
- 🧠 **Verify manually** — automated tools surface leads, not confirmed vulnerabilities. Always validate findings before reporting
- 📝 **Document everything** — keep notes per target for accurate bug bounty reports

---

<div align="center">

[← Back to README](README.md) · [Requirements](requirements.md)

<sub>Shadow Recon © 2025 Nishant Padha</sub>

</div>
