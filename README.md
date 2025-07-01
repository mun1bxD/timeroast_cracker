Sure! Here's how the structure of your tool will look, along with a clean layout of files, content, and how it feels when someone runs or uses it.

---

## 📁 **Directory Layout**

```
timeroast_cracker/
├── timeroast_cracker.py         # 🔓 The main cracking script
├── requirements.txt             # 📦 Python dependencies
├── hashes.txt                   # 🧊 Timeroast hash file (example)
├── rockyou.txt                  # 🔑 Wordlist (symlink or download)
└── README.md                    # 📘 Tool description and usage instructions
```

---

## 🔓 **timeroast\_cracker.py (Tool Name)**

A Python tool that cracks **MS-SNTP hashes** from **Timeroast attacks** using a wordlist or single password.

It prints results like:

```bash
$ python3 timeroast_cracker.py -H hashes.txt -w /usr/share/wordlists/rockyou.txt

[*] Cracking RID 1000...
🔍 RID 1000:  10%|████▌                                | 140000/1400000 [00:02<00:18, 75000pw/s]
[-] Password for RID 1000 not found in wordlist.

[*] Cracking RID 1144...
🔍 RID 1144:  45%|█████████████▎                       | 630000/1400000 [00:05<00:06, 110000pw/s]
[+] Password for RID 1144: monkey123
```

---

## 📘 **README.md Preview**

````markdown
# ⏱️ Timeroast Password Cracker

This is a lightweight Python script that cracks MS-SNTP hashes obtained from the Timeroast attack against Active Directory domain controllers.

## Features
- Supports hash format: `RID:$sntp-ms$HASH$SALT`
- Wordlist-based and single password cracking
- Shows dynamic progress bar with `tqdm`
- Fallback support for MD4 with `passlib`

## Usage

```bash
python3 timeroast_cracker.py -H hashes.txt -w /usr/share/wordlists/rockyou.txt
````

```bash
python3 timeroast_cracker.py --hash "1144:$sntp-ms$deadbeef$saltsalt" --password 'P@ssword'
```

## Installation

```bash
pip install -r requirements.txt
```

## Requirements

* Python 3.6+
* tqdm
* passlib (optional for fallback MD4)

````

---

## 📦 requirements.txt

```text
tqdm>=4.0.0
passlib>=1.7.0
````

---

Let me know if you want:

* ✅ To generate this as a zipped folder
* ✅ Auto-download of `rockyou.txt` if not found
* ✅ To convert this into a command-line tool with `setup.py` or `argcomplete`

Would you like a full README.md file written out too?
