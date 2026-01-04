# Applied Cryptography in Real-World Scenarios 


project links: https://docs.google.com/document/d/1UzXPa88Nr6BBdjqF_ZTYBT0je7yzeuz1IJXuqICREzY/edit?usp=drive_link
https://docs.google.com/presentation/d/1OOl1pTN426pEEVsqRiw1QG4BFIg4x3MX/edit?usp=drive_link&ouid=117641853008852879405&rtpof=true&sd=true


##  Project Overview
This project simulates the role of a **Lead Security Officer** at *Nexus Dynamics*, a financial firm. The objective was to demonstrate the practical application of cryptographic primitives to secure corporate data against specific threats such as physical theft, insider fraud, and network sniffing.

**Role:** Lead Security Officer  
**Tools Used:** Git Bash, OpenSSL, SHA-256, Windows CLI  
**Key Concepts:** Confidentiality (AES-256), Integrity (Hashing), Secure Messaging (RSA), Non-Repudiation (Digital Signatures)

---

##  Scenarios & Solutions

### 1. Confidentiality: The "Lost Laptop" Crisis 
**Threat:** An intern lost a laptop containing a plain-text file (`secret.txt`) with corporate credit card PINs.
**Solution (AES-256):** - Applied **Symmetric Encryption** using OpenSSL before the device was lost.
- **Outcome:** The thief only sees `secret.enc` (encrypted ciphertext). Without the password/key, the data is unreadable, protecting the firm's assets.

### 2. Integrity: The "Greedy Relative" Plot 
**Threat:** A relative presented a modified "Last Will and Testament" to claim an inheritance, altering the age/beneficiary details.
**Solution (SHA-256 Hashing):** - Generated a **Hash (Digital Fingerprint)** of the original document.
- Compared it against the hash of the relative's document.
- **Outcome:** The hashes did not match, instantly proving the file was tampered with.

### 3. Secure Messaging: The "VIP Safe House" Extraction 
**Threat:** A high-profile whistleblower ("The Asset") is in a location with tapped phone lines. The extraction team needs the location ("Third Floor"), but unencrypted messages will be intercepted.
**Solution (Asymmetric Encryption/PKI):** - Encrypted the location message using the Team Lead’s **Public Key**.
- **Outcome:** Interceptors see only scrambled ciphertext. Only the Team Lead (with the **Private Key**) can decrypt and read the location.

### 4. Authenticity: The "Disputed Contract" 
**Threat:** A vendor attempts to repudiate a signed agreement, claiming they never signed that specific version.
**Solution (Digital Signatures):** - The document was cryptographically signed using the sender's **Private Key**.
- **Outcome:** Verification with the Public Key returned "Verified OK", mathematically proving the sender's identity and that the document was not altered.

---

##  Technical Implementation
The project was executed using command-line interface (CLI) tools to perform cryptographic operations.

**Sample Commands Used:**
```bash
# Encrypting a file (AES-256)
openssl enc -aes-256-cbc -salt -in secret.txt -out secret.enc

# Decrypting a file
openssl enc -aes-256-cbc -d -in secret.enc -out secret_unlocked.txt

# Generating a File Hash
sha256sum "Last_Will.docx"

Lessons Learned
File Locking: Encountered OS-level file locking issues when trying to encrypt open Word documents. Learned that files must be closed in applications before CLI manipulation.

Key Management: Practical experience in handling Public vs. Private keys is critical; losing a Private Key means permanent data loss.

Repository Contents
User Guide: Step-by-step documentation on encryption/hashing procedures.

Evidence Screenshots: https://docs.google.com/document/d/1UzXPa88Nr6BBdjqF_ZTYBT0je7yzeuz1IJXuqICREzY/edit?usp=drive_link
https://docs.google.com/presentation/d/1OOl1pTN426pEEVsqRiw1QG4BFIg4x3MX/edit?usp=drive_link&ouid=117641853008852879405&rtpof=true&sd=true



