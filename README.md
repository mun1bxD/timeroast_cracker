# ⏱️ Timeroast Password Cracker

A lightweight and powerful Python tool for cracking MS-SNTP password hashes obtained via the **Timeroast attack** on Active Directory environments.

This tool is ideal for red teamers, penetration testers, and researchers performing targeted credential attacks against domain-joined systems that have been coerced into revealing time-based authentication hashes.

---

##  Features

-  Supports MS-SNTP hash format: `RID:$sntp-ms$HASH$SALT`
-  Crack hashes using a wordlist (e.g., rockyou.txt)
-  Test a single password against one or more hashes
-  Real-time progress bar using `tqdm`
-  Handles large hash sets and wordlists efficiently
-  Fallback to `passlib` for systems without native `md4` support

---

##  Requirements

- Python 3
- [tqdm](https://pypi.org/project/tqdm/)
- [passlib](https://pypi.org/project/passlib/) (optional fallback for MD4)

Install requirements:

```bash
pip install -r requirements.txt
````

---

## File Format

Each hash line must be in the following format:

```text
RID:$sntp-ms$<hash>$<salt>
```

Example:

```text
1144:$sntp-ms$9fb07ac2e476386ff4d4fd03162b3d74$1c0111e9...dcbebdc110d
```

---

##  Usage Examples

#### Crack hashes from file using a wordlist

```bash
python3 timeroast_cracker.py -H hashes -w /usr/share/wordlists/rockyou.txt
```

#### Test a single password against multiple hashes

```bash
python3 timeroast_cracker.py -H hashes --password Password123
```

#### Crack a single hash

```bash
python3 timeroast_cracker.py --hash "1144:$sntp-ms$abc123...$deadbeef..." -w rockyou.txt
```

#### Help Menu

```bash
python3 timeroast_cracker.py --help
```

---

##  Background

Timeroasting is a technique that abuses the MS-SNTP authentication mechanism in Active Directory environments. When certain account attributes are misconfigured (or manipulated by a privileged user), domain controllers may return MD5-based challenge-response hashes for accounts that normally wouldn’t be vulnerable. These hashes can be cracked offline to retrieve the cleartext password.

Inspired by:

* Timeroast attack by [Tom Tervoort (Secura)](https://www.secura.com/uploads/whitepapers/Secura-WP-Timeroasting-v3.pdf)

