## 🗓️ Day 45/100 – Cryptography Basics & Weak Encryption Risks

**Focus:** Understanding core crypto building blocks and how weak choices expose data.

### 🔑 Core Concepts

#### 1. Hashing (One-Way)
- Used for **integrity** and **password storage**.
- Example algorithms: `SHA-256`, `bcrypt`, `Argon2`.
- Good practice:
  - Always use a **salt**.
  - Prefer slow, adaptive functions (bcrypt/Argon2) over fast hashes.

#### 2. Encryption (Two-Way)
- Used for **confidentiality**.
- **Symmetric:** Same key for encrypt/decrypt (e.g., `AES-256`).
- **Asymmetric:** Public key to encrypt, private key to decrypt (e.g., `RSA`, `ECC`).

### ⚠️ How Weak Encryption Fails

1. **Legacy Algorithms**
   - MD5 / SHA-1: vulnerable to collisions and fast to brute force.
   - DES/3DES: key sizes too small by modern standards.
   - Outcome: Passwords and data can be recovered with commodity hardware.

2. **Poor Password Storage**
   - Storing passwords as:
     - Plaintext
     - Unsalted MD5 / SHA-1
   - Attackers use rainbow tables and GPU rigs to crack them very quickly.

3. **Weak TLS / Transport Security**
   - Allowing outdated protocols (e.g., TLS 1.0/1.1) or weak cipher suites.
   - Makes encrypted traffic vulnerable to downgrade and interception attacks.

### 🧠 Security Takeaways

- For passwords, use:
  - `bcrypt`, `scrypt`, or `Argon2` with unique salts.
- For data encryption:
  - AES-256 in authenticated modes (e.g., GCM).
- For transport:
  - Enforce modern TLS versions and strong cipher suites.
- Assume attackers **can** brute force weak crypto given time and hardware.

**Day 45 Summary:**  
Learning crypto basics makes it clear: most “crypto failures” are not math problems, they are **bad choices and configurations**.
