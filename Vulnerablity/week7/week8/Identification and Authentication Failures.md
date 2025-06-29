# MSSE-642 Software Assurance


# June-29, 2025


# Randall Granier
 
 # Security Risk Analysis: Identification and Authentication Failures



## Introduction & Description


Identification and Authentication Failures—previously known as Broken Authentication—refer to weaknesses in how applications confirm user identities and manage sessions. These failures allow attackers to impersonate users, bypass authentication, or hijack active sessions, leading to unauthorized access to sensitive systems and data. Common flaws include weak password policies, lack of multi-factor authentication (MFA), improper session handling, and exposure of session identifiers in URLs.


**Example of a Vulnerable Authentication Flow** 

![My Photo](auth.PNG)
This example is vulnerable to brute-force and credential stuffing attacks, and lacks MFA or secure session management.
Specific Real-World Example


**Twitter (2020):**


In July 2020, attackers managed to compromise Twitter’s internal tools using a social engineering attack, successfully bypassing authentication controls. They gained access to high-profile accounts like those of Barack Obama and Elon Musk, and posted cryptocurrency scams. This breach was made possible by weak internal authentication, the absence of strong MFA enforcement, and inadequate monitoring. It became a significant global incident with regulatory implications scrutiny.


**Analysis:**

How to Prevent Identification and Authentication Failures


**Enforce strict password policies:** Require complex passwords and ban commonly used or default credentials (e.g., “admin/admin” or “Password1”).


**Enable Multi-Factor Authentication (MFA) for all users:** This requires a minimum of two verification methods, particularly for admin and sensitive accounts.


**Restrict Authentication Attempts:** 

Implement rate limiting and account lockouts to stop brute-force and credential stuffing attacks.
For secure credential storage, always use strong, salted hash functions like bcrypt or Argon2 to protect passwords—never keep them in plain text or with weak hashes.


**Monitor and Alert:** Track login attempts and flag suspicious activity, like repeated failed logins or access from unfamiliar locations.
Protect Recovery Mechanisms: Steer clear of insecure password recovery methods, such as knowledge-based questions, and opt for secure, time-limited reset links instead.


**Conclusion**
Identification and Authentication Failures pose a significant security threat, allowing attackers to impersonate users, gain unauthorized access, and leak sensitive information. High-profile breaches, like the 2020 Twitter incident, show the severe consequences of weak authentication measures. To mitigate this risk, organisations need to implement strong password policies, multi-factor authentication, secure session management, and regular monitoring. By strictly enforcing these controls, organisations can greatly reduce the risk of unauthorised access and follow OWASP’s guidelines for secure authentication.
