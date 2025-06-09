#### [🔙 Back to README](../../README.md)

# Cryptographic Failures

## Introduction & Description

Cryptographic failures happen when sensitive data—like passwords, tokens, or personal information—is not properly protected in transit or at rest. These failures are often due to:

- Use of outdated or broken encryption algorithms
- Storing data in plaintext
- Misconfigured TLS/SSL implementations
- Poor key management practices

Insecure cryptographic design undermines trust in software systems. If attackers can intercept, decrypt, or access protected data due to weak encryption or missing controls, the consequences can include identity theft, credential leaks, account takeover, and regulatory violations.

## Where Encryption Matters in the Data Flow

To maintain secure data handling, encryption should be enforced at multiple stages of the user–system interaction:

- **Client to Server (Transit):**
  - Use HTTPS/TLS to encrypt traffic between browser/mobile apps and backend servers.
  - Prevents interception via man-in-the-middle (MITM) attacks.

- **Server Memory (Processing):**
  - Encrypt or hash sensitive values like passwords before they touch business logic.
  - Example: Hashing passwords using bcrypt before authentication logic is run.

- **Server to Database (Transit):**
  - Use database connectors that support TLS to encrypt traffic between app servers and database systems.
  - Protects against internal network sniffing.

- **At Rest (Storage):**
  - Encrypt sensitive fields in the database (e.g., SSNs, tokens).
  - Use strong, vetted encryption standards (AES-256, RSA, etc.).
  - Store passwords only as salted hashes (e.g., bcrypt, Argon2), never plaintext or reversible encryption.

- **Backups & Logs:**
  - Encrypt backup files and avoid logging sensitive data.
  - Misconfigured logging is a common leak vector.

**Example:**  
A login form transmitting credentials over unencrypted HTTP:

```html
<!-- Insecure form -->
<form action="http://example.com/login" method="POST">
  <input type="text" name="username">
  <input type="password" name="password">
  <button type="submit">Login</button>
</form>
```

This sends sensitive information in plain text, allowing attackers on the same network to capture credentials using simple tools.

Modern applications are expected to follow secure-by-default practices and use mature cryptographic libraries. When those expectations are violated—as seen in several high-profile incidents—user data and company credibility are both at risk.

More at: [OWASP Cryptographic Failures](https://owasp.org/Top10/A02_2021-Cryptographic_Failures/)

---

## Specific Real-World Example

### Summary

In April 2019, Facebook faced a major cryptographic failure—not because their core platform was directly hacked, but due to improper handling of user data by third-party developers with access to Facebook’s ecosystem. Security researchers at [UpGuard](https://www.upguard.com/breaches/facebook-user-data-leak) discovered over **540 million Facebook-related records** publicly exposed through unsecured Amazon S3 buckets. These buckets were not encrypted and had no access restrictions.

The breach highlighted Facebook’s failure to enforce encryption and data governance standards across its developer ecosystem. Although the data wasn't directly exposed by Facebook’s infrastructure, the data originated from Facebook APIs and was collected through platform integrations, pointing to a systemic failure in controlling and protecting user data.

---

### Exposure Details: Cultura Colectiva and At the Pool

- **Cultura Colectiva**, a Mexico-based media company, exposed over **146 GB of Facebook data** including user IDs, reactions, account names, and more in plaintext via an open Amazon S3 bucket. This data was collected using Facebook’s developer tools but stored with no encryption or security controls.

- A second data set came from a now-defunct app called **“At the Pool.”** The backup included fields such as `fb_user`, `fb_likes`, `fb_photos`, and `password`. According to UpGuard, “The passwords are presumably for the ‘At the Pool’ app rather than for the user’s Facebook account, but would put users at risk who have reused the same password across accounts.”

Both datasets were discovered by [UpGuard](https://www.upguard.com/breaches/facebook-user-data-leak) in early 2019 and were stored on Amazon S3, a cloud service that requires proper configuration by the data owner. In both cases, the configuration failed.

---

### Internal Facebook Logging Failure ([KrebsOnSecurity](https://krebsonsecurity.com/2019/03/facebook-stored-hundreds-of-millions-of-user-passwords-in-plain-text/))

In addition to the publicly exposed third-party data discovered by UpGuard, Facebook itself was the subject of a cryptographic failure reported by KrebsOnSecurity in March 2019. This incident involved internal Facebook systems and directly implicated the company’s own development practices.

> “Facebook is probing a series of security failures in which employees built applications that logged unencrypted password data for Facebook users and stored it in plain text on internal company servers.”  
> — [KrebsOnSecurity](https://krebsonsecurity.com/2019/03/facebook-stored-hundreds-of-millions-of-user-passwords-in-plain-text/), March 21, 2019

A senior Facebook employee, speaking anonymously, said the investigation revealed that between **200 million and 600 million user passwords** were stored in plain text and were searchable by over **20,000 Facebook employees**. The investigation found internal archives containing plaintext passwords dating back to 2012.

> “Access logs showed some 2,000 engineers or developers made approximately nine million internal queries for data elements that contained plain text user passwords.”

This event underscores a separate but equally significant cryptographic failure—one that originated from within Facebook’s engineering processes, highlighting both cultural and procedural shortcomings in safeguarding sensitive user credentials.

---

### Attribution Uncertainty

The [Wired report](https://www.wired.com/story/facebook-data-leak-500-million-users-phone-numbers/?_sp=ca577bfa-77db-4f35-981a-5eb851502120.1748024163536) emphasized the lack of clarity around who was responsible for scraping and exposing this data:

> “There’s still no definitive evidence of who scraped the data, when, or exactly how, despite its clear ties to Facebook data.”

This points to a deeper issue: Facebook’s platform allowed massive amounts of user data to be collected by third parties, with minimal long-term oversight. The breach underscores the consequences of failing to enforce cryptographic controls and storage compliance after data leaves a platform’s boundaries.

---

### Incident Response Timeline

The [UpGuard report](https://www.upguard.com/breaches/facebook-user-data-leak) outlines the months-long struggle to get the exposed data secured:

- **Jan 10 & 14, 2019:** UpGuard contacts Cultura Colectiva. No response.
- **Jan 28:** UpGuard contacts Amazon Web Services (AWS).
- **Feb 1:** AWS informs UpGuard that the bucket owner has been notified.
- **Feb 21:** UpGuard follows up; AWS agrees to escalate the issue.
- **April 3, 2019:** Only after Bloomberg contacts Facebook for comment is the bucket `cc-datalake` secured.

> “It was not until the morning of April 3rd, 2019, after Facebook was contacted by Bloomberg for comment, that the database backup, inside an AWS S3 storage bucket titled ‘cc-datalake,’ was finally secured.”  
> — [UpGuard](https://www.upguard.com/breaches/facebook-user-data-leak)

In contrast, the “At the Pool” data had already gone offline during UpGuard’s research, though it is unclear if this was due to responsible action or coincidence. UpGuard noted:

> “It is unknown if this is a coincidence, if there was a hosting period lapse, or if a responsible party became aware of the exposure at that time.”

---

**Sources:**

- [Krebs on Security: Facebook Stored Hundreds of Millions of User Passwords in Plain Text for Years](https://krebsonsecurity.com/2019/03/facebook-stored-hundreds-of-millions-of-user-passwords-in-plain-text/)
- [Wired: What Really Caused Facebook's 500M-User Data Leak?](https://www.wired.com/story/facebook-data-leak-500-million-users-phone-numbers/?_sp=ca577bfa-77db-4f35-981a-5eb851502120.1748024163536)
- [UpGuard: Losing Face: Two More Cases of Third-Party Facebook App Data Exposure](https://www.upguard.com/breaches/facebook-user-data-leak)

---

## Analysis About How to Prevent

- Store passwords using strong hashing algorithms (e.g., bcrypt, Argon2).
- Use TLS for all data in transit.
- Never store sensitive data unencrypted.
- Enforce key management policies and regularly rotate keys.
- Avoid custom encryption; use vetted libraries (e.g., libsodium, OpenSSL).

Refer to: [OWASP Cryptographic Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html)

---

## My Thoughts

This was an interesting "hack" to look into, but the more I dug, the harder it became to find concrete details about the vulnerable systems. I kept finding more and more possible sources and angles from Facebook’s side—third-party developers, storage misconfigurations, unclear ownership, but I couldn’t find one reliable place that summarized everything clearly. That was frustrating.

As a student actively trying to learn more about cybersecurity—not a journalist or investigative reporter—I would have appreciated a single trusted source that broke down the technical stack, timelines, and responsibilities. I understand (or at least vaguely appreciate) why corporations are often secretive, and maybe I’m naive to wish for such transparency. Still, centralizing the known facts would help learners and professionals alike better understand what went wrong and how to prevent it.

---

## Conclusion / Closing

Cryptographic failures, whether due to plaintext storage, weak algorithms, or misconfigured access, leave sensitive data vulnerable to exposure. These lapses not only compromise user privacy but also damage organizational credibility and compliance. Implementing strong encryption, secure key management, and end-to-end data protection is essential. Consistently applying modern cryptographic best practices reduces the risk of breaches and builds long-term trust in the systems we design.

---

## References / ChatGPT Analysis

This report was researched and written using verified sources and refined with the help of ChatGPT 4.0 for drafting and revision. GitHub Copilot in VS Code was used to assist with Markdown formatting and style consistency. All external facts were cross-checked with credible sources found online. 

**References:**

* OWASP Top 10: [https://owasp.org/Top10/A02_2021-Cryptographic_Failures/](https://owasp.org/Top10/A02_2021-Cryptographic_Failures/)
* OWASP Crypto Cheat Sheet: [https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html)
* 2019. Facebook Stored Hundreds of Millions of User Passwords in Plain Text for Years: [https://krebsonsecurity.com/2019/03/facebook-stored-hundreds-of-millions-of-user-passwords-in-plain-text/](https://krebsonsecurity.com/2019/03/facebook-stored-hundreds-of-millions-of-user-passwords-in-plain-text/)
* 2021. What Really Caused Facebook's 500M-User Data Leak? [https://krebsonsecurity.com/2019/03/facebook-stored-hundreds-of-millions-of-user-passwords-in-plain-text/](https://krebsonsecurity.com/2019/03/facebook-stored-hundreds-of-millions-of-user-passwords-in-plain-text/)
* 2019. Losing Face: Two More Cases of Third-Party Facebook App Data Exposure [https://www.upguard.com/breaches/facebook-user-data-leak](https://www.upguard.com/breaches/facebook-user-data-leak)
* Hoffman, A. (2020). *Web Application Security: Exploitation and Countermeasures for JavaScript Apps*. O’Reilly Media.
