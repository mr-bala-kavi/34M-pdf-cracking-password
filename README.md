# 34M PDF Cracking Password Wordlist

A password wordlist collection for **authorized** PDF password recovery and security testing. Contains ~34 million candidate passwords compiled from common, leaked, and frequently-used credentials.

## Contents

| File | Entries | Description |
|------|---------|-------------|
| `pdf-crack-10k.txt` | 10,000 | Top 10k most common passwords — fast first-pass dictionary |
| `pdf-crack-wordlist.txt` | 34,291,013 | Full ~34M password wordlist (large file, not tracked in Git) |

> The full `pdf-crack-wordlist.txt` (~360 MB) exceeds GitHub's file-size limit and is excluded via `.gitignore`.
> **Download it from the [latest release](../../releases/latest).**

## Usage

These wordlists are intended for use with PDF password recovery tools such as `pdfcrack`, `John the Ripper`, or `hashcat`.

### pdfcrack

```bash
pdfcrack -f protected.pdf -w pdf-crack-10k.txt
```

### John the Ripper

<img src="john-logo.svg" alt="John the Ripper" width="120" align="right" />

This wordlist is built primarily for **John the Ripper** — the passwords here feed its dictionary attack against PDF hashes.

```bash
# Extract the hash
pdf2john protected.pdf > hash.txt

# Run dictionary attack
john --wordlist=pdf-crack-wordlist.txt hash.txt
```

### hashcat

```bash
# -m 10500 for PDF 1.4-1.6 (Acrobat 5-8); choose the mode for your PDF version
hashcat -m 10500 hash.txt pdf-crack-wordlist.txt
```

## Recommended workflow

1. Start with `pdf-crack-10k.txt` for a quick pass — most weak passwords fall here.
2. If unsuccessful, run the full `pdf-crack-wordlist.txt`.
3. Combine with rule-based mutations for better coverage.

## ⚠️ Legal & Ethical Notice

This project is provided **strictly for legitimate purposes**, including:

- Recovering access to your **own** password-protected PDF files
- **Authorized** penetration testing and security assessments
- Security research and education

**Do not** use these wordlists to access files you do not own or lack explicit written permission to test. Unauthorized access to computer systems and data is illegal in most jurisdictions. The authors assume no liability for misuse.

## License

Provided as-is for educational and authorized security-testing use.
