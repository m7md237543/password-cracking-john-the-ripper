# Password Cracking Lab – John the Ripper

A hands-on cybersecurity lab project for the "Introduction to Cyber Security" 
course at Umm Al-Qura University. The project demonstrates how password-protected 
PDF files can be cracked using John the Ripper, and highlights the importance of 
strong passwords.

## Objective
Test how password strength affects the time and difficulty of cracking it, 
using two different attack methods on a protected PDF file.

## Environment
- **VirtualBox** (virtual machine)
- **Kali Linux**
- **John the Ripper** (password cracking tool)

## Steps

**1. Install the tool:**
```bash
sudo apt install john
```

**2. Extract the password hash from a protected PDF:**
```bash
pdf2john test.pdf > pdf_hash.txt
```

**3. Attack 1 – Dictionary Attack (using the rockyou wordlist):**
```bash
john --wordlist=/usr/share/wordlists/rockyou.txt pdf_hash.txt
```

**4. Attack 2 – Mask Attack (for a 5-digit numeric password):**
```bash
john --mask='?d?d?d?d?d' hash_5digit.txt
```

**5. Show the cracked password:**
```bash
john --show --format=PDF hash_5digit.txt
```

## Results
- Weak passwords (short / numeric only) were cracked quickly using the mask attack.
- Stronger passwords took significantly more time and resources.
- This shows that password **length and complexity** are the main factors in resisting cracking attempts.

## Key Concepts
- **Hash:** the encrypted form of a password.
- **Dictionary Attack:** trying passwords from a prepared wordlist.
- **Mask Attack:** trying all combinations that match a known pattern.

## Tools Compared (from the project research)
| Tool | Best Use |
|------|----------|
| John the Ripper | CPU-based cracking & hash extraction |
| Hashcat | GPU-based, high-speed cracking |
| Hydra | Online/network login attacks |

## Note
This project was conducted in an isolated virtual environment for **educational 
purposes only**, as part of a university course. It was a team project; I led 
the full technical implementation.
