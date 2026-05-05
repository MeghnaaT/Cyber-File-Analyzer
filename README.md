# 🔐 CyberGuard AI — Cyber Threat Intelligence Platform

<p align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Flask-000000?style=flat&logo=flask"/>
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black"/>
  <img src="https://img.shields.io/badge/OSINT-Threat%20Intelligence-red?style=flat"/>
  <img src="https://img.shields.io/badge/License-MIT-lightgrey?style=flat"/>
</p>

A full-stack cybersecurity intelligence platform for analyzing URLs, files, IP addresses, domains, and email headers. Built on OSINT techniques and heuristic threat modeling, it produces a unified risk score (0–100) and automated PDF threat reports with AI-assisted explanations.

---

## 🎯 What It Does

CyberGuard AI is a one-stop threat analysis dashboard. Analysts and security researchers can paste a suspicious URL, upload a file, or input an email header and receive a structured threat report in seconds — without needing to query multiple external tools manually.

---

## ✨ Features

### 🔗 URL / Domain Analysis
- Phishing detection: brand similarity scoring, suspicious TLD matching, Unicode homoglyph detection
- SSL certificate validation (issuer, expiry, mismatch)
- DNS record extraction (A, MX, NS, TXT)
- WHOIS data lookup
- Redirect chain tracing

### 📁 File Analysis
- SHA-256 and MD5 hash computation
- Entropy scoring to detect packed/encrypted payloads
- File type identification independent of extension
- Comparison against local known-malicious hash list

### 🌐 IP Address Intelligence
- Reverse DNS lookup
- ASN and geolocation data
- Open port fingerprinting (via socket probing)
- Reputation check against blocklist feeds

### 📧 Email Header Forensics
- SPF record validation
- DKIM signature verification
- DMARC policy lookup
- Header hop analysis for relay spoofing detection

### 📊 Unified Risk Scoring
- All signals aggregated into a 0–100 risk score
- Risk bands: Low (0–30) / Medium (31–60) / High (61–80) / Critical (81–100)
- Factor-by-factor breakdown with severity weights

### 📄 Automated PDF Reporting
- One-click export of full threat report
- AI-assisted plain-language explanation of findings
- Structured for sharing with non-technical stakeholders

---

## 🏗️ Architecture

```
Browser (Vanilla JS + CSS)
        │
        ▼ REST API
Flask Backend
  ├── /analyze/url        → phishing + SSL + DNS + WHOIS
  ├── /analyze/file       → hash + entropy + type detection
  ├── /analyze/ip         → geolocation + ASN + ports
  ├── /analyze/email      → SPF/DKIM/DMARC + header forensics
  └── /report/generate    → PDF report + AI explanation
        │
        ▼
  OSINT Modules (pure Python)
  Risk Scoring Engine
  PDF Generator (reportlab / weasyprint)
```

---

## 🚀 Getting Started

### Prerequisites

```bash
Python 3.9+
pip install flask requests dnspython python-whois reportlab pyOpenSSL
```

### Installation

```bash
git clone https://github.com/MeghnaaT/CyberGaurd-AI-Powered-Cyber-Security-Command-Center-.git
cd CyberGaurd-AI-Powered-Cyber-Security-Command-Center-
pip install -r requirements.txt
python app.py
```

Visit `http://localhost:5000` in your browser.

---

## 📁 Repository Structure

```
├── app.py                  # Flask application entry point
├── modules/
│   ├── url_analyzer.py     # Phishing detection, SSL, DNS
│   ├── file_analyzer.py    # Hash, entropy, file type
│   ├── ip_analyzer.py      # Geolocation, ASN, ports
│   └── email_analyzer.py   # SPF/DKIM/DMARC forensics
├── scoring/
│   └── risk_engine.py      # Unified 0–100 risk scoring
├── reporting/
│   └── pdf_generator.py    # PDF threat report generation
├── static/                 # Frontend JS + CSS
├── templates/              # Flask HTML templates
├── requirements.txt
└── README.md
```

---

## 🧪 Testing

```bash
# Run analysis on a test phishing URL
curl -X POST http://localhost:5000/analyze/url \
  -H "Content-Type: application/json" \
  -d '{"url": "http://paypa1.com/login"}'
```

Sample risk scores observed during testing:
- Known phishing domains: 75–95 / 100
- Legitimate domains (google.com, github.com): 2–8 / 100
- Ambiguous / new domains: 30–55 / 100

---

## 🔮 Planned Improvements

- [ ] VirusTotal API integration for file hash enrichment
- [ ] Shodan API integration for IP intelligence
- [ ] YARA rule scanning for malware signatures
- [ ] User accounts with saved scan history
- [ ] Docker containerization for portable deployment

---

## ⚠️ Responsible Use

This tool is intended for **defensive security research, education, and ethical threat analysis** only. Do not use it to analyze systems or networks you do not have permission to test.

---

## 🤝 Contributing

Issues and PRs are welcome. Please open an issue before submitting a large change.

1. Fork the repository
2. Create a branch: `git checkout -b feat/your-feature`
3. Commit: `git commit -m "feat: add VirusTotal hash enrichment"`
4. Open a PR against `main`

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

*Built by [Meghna Tiwari](https://github.com/MeghnaaT)*

