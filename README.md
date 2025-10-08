# Using-tools-like-John-the-Ripper-for-password-cracking
## AIM:
To crack password hashes using John the Ripper in Kali Linux.
## REQUIREMENTS:
- **Operating System:** Kali Linux / Ubuntu / Windows (with JtR binaries)
- **Tools:**
    - John the Ripper (Community/Pro version)
    - Hash generating tools (e.g., openssl, unshadow)
- **Test Data:**
    - /etc/shadow file (Linux hashed passwords)
    - Custom password-protected file (ZIP, RAR, etc.)
## ARCHITECTURE DIAGRAM:
```mermaid
flowchart TD
    A[Password Protected File / Hash] --> B[John the Ripper]
    B --> C[Select Attack Mode: Dictionary or Brute Force]
    C --> D[Load Wordlist / Charset Rules]
    D --> E[Password Cracking Process]
    E --> F[Recovered Passwords]
```
## DESIGN STEPS:
### Step 1: Install John the Ripper
```bash
sudo apt update
sudo apt install john -y
```

### Step 2: Prepare Hash File
- Extract hashes (Linux example):
```
unshadow /etc/passwd /etc/shadow > myhashes.txt
```
- For a ZIP file:
```
zip2john secret.zip > ziphash.txt
```
### Step 3: Run John the Ripper
- Dictionary Attack:
```
john --wordlist=/usr/share/wordlists/rockyou.txt myhashes.txt
```
- Brute Force (Incremental Mode):
```
john --incremental myhashes.txt
```
### Step 4: Show Cracked Passwords
```
john --show myhashes.txt
```
## PROGRAM:
1. **Hash Extraction** – Obtain password hashes from system files or encrypted archives.
2. **Attack Mode Selection** – Choose between dictionary, brute force, or hybrid.
3. **Cracking Phase** – John the Ripper runs through candidate passwords.
4. **Password Recovery** – Successfully cracked passwords are displayed.

## OUTPUT:
Cracked Passwords from Hash File
<img width="1920" height="937" alt="create document" src="https://github.com/user-attachments/assets/166d8be1-f41d-473d-956b-e93a536f0132" />
<img width="1920" height="937" alt="mousepad" src="https://github.com/user-attachments/assets/771f2d07-0cb4-4a7e-b222-3247aa8294d5" />

<img width="1920" height="937" alt="create password" src="https://github.com/user-attachments/assets/041d27de-6975-48a1-baa5-fcaa7ad9d287" />
<img width="1920" height="937" alt="create archieve" src="https://github.com/user-attachments/assets/1001782d-de6e-410e-b990-ec3adaaa2413" />

<img width="1920" height="937" alt="hash txt" src="https://github.com/user-attachments/assets/2ae1a149-efd3-4ed1-a768-74e5af0ad167" />
<img width="955" height="925" alt="password crack" src="https://github.com/user-attachments/assets/926db325-e5ee-437d-ab48-c323dbea571f" />

## RESULT:
The password hashes were successfully cracked using John the Ripper.

