## 🗓️ Day 61/100 – JWT Attacks & Token Security

**Focus:** Understanding how JWTs can be attacked and how to use them more safely.

### 🧨 Attack Surfaces

- `alg: none` and Algorithm Confusion
  - Some implementations historically allowed `alg: none`, meaning no signature verification.
  - Others were vulnerable to HS256/RS256 confusion:
    - Server expects RS256 but accepts HS256 and uses the RSA public key as an HMAC secret, allowing forged tokens.

- Weak Secrets
  - Short or guessable HMAC secrets for HS256 tokens make brute-force/signing feasible.

- Header Parameter Abuse
  - `kid` header used to look up keys:
    - Path traversal or arbitrary file reads.
    - Pointing to attacker-controlled resources.
  - Other custom headers that influence key selection or verification logic.

### 🛡️ Safer JWT Usage

- Algorithms & Keys
  - Explicitly whitelist allowed algorithms.
  - Prefer RS256 with strong key management for larger systems.
  - Rotate keys periodically and on suspicion of compromise.

- Validation
  - Always verify:
    - Signature
    - `iss` (issuer)
    - `aud` (audience)
    - `exp`, `nbf`, and other relevant claims
  - Reject tokens using unexpected algorithms or missing critical claims.

- Design Considerations
  - Keep token lifetimes short.
  - Avoid placing highly sensitive or rapidly-changing authorization data inside JWTs when revocation is hard.
  - Treat tokens as secrets: protect in transit (HTTPS) and at rest (secure storage, HttpOnly cookies if used in browsers).

**Day 61 Summary:**
JWTs are just envelopes; the real security is in how strictly you verify them and how carefully you manage the keys behind them.
