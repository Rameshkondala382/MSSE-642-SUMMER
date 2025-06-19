#### [🔙 Back to README](../../README.md)

# Vulnerable and Outdated Components

## Introduction & Description

Vulnerable and outdated components refer to libraries, frameworks, platforms, and other dependencies that contain known security flaws but are still used in production environments. These flaws may be due to unpatched vulnerabilities, deprecated software, or reliance on components no longer maintained by their creators.

Common causes include:

- Not updating dependencies regularly
- Using software beyond its end-of-life (EOL)
- Failing to monitor vulnerability databases (e.g., CVE, NVD)
- Blindly trusting third-party packages without review

**Example:**  
A web application uses an outdated version of jQuery with a known XSS vulnerability. An attacker exploits this to inject malicious scripts into users' browsers, leading to session hijacking or data theft.

More at: [OWASP A06:2021 – Vulnerable and Outdated Components](https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/)

## Specific Real-World Example: Equifax Apache Struts Vulnerability (2017)

One of the most widely cited examples of this issue is the **Equifax breach of 2017**, where attackers exploited a known vulnerability in **Apache Struts (CVE-2017-5638)** — a popular Java web framework.

Despite the vulnerability being publicly disclosed in **March 2017** and patches being available, Equifax failed to apply the update in a timely manner. Hackers were able to exploit the flaw using a crafted HTTP request, giving them remote code execution (RCE) capabilities on Equifax’s systems. This led to the exfiltration of sensitive personal data belonging to **147 million people**, including Social Security numbers, dates of birth, and driver’s license numbers.

> “The vulnerability was disclosed publicly, and a patch was issued. However, Equifax failed to identify and patch the vulnerable systems in time.”  
> — [U.S. House Oversight Report](https://oversight.house.gov/wp-content/uploads/2018/12/Equifax-Report.pdf)

This case illustrates how the use of outdated components — especially those exposed to the internet — can lead to catastrophic consequences when security updates are ignored.

## Analysis About How to Prevent

To prevent exploitation from vulnerable or outdated components:

- **Maintain a current software inventory**, including third-party libraries and their versions.
- **Subscribe to vulnerability feeds** (e.g., CVE/NVD, GitHub Security Advisories).
- Use **automated tools** to scan for known vulnerabilities (e.g., Snyk, Dependabot, OWASP Dependency-Check).
- Apply **patches and security updates** regularly — don’t delay.
- Avoid using libraries that are no longer maintained or have reached end-of-life (EOL).
- Use **Software Bill of Materials (SBOMs)** to track dependency provenance in modern CI/CD pipelines.

Refer to: [OWASP Dependency-Check](https://owasp.org/www-project-dependency-check/)

## My Thoughts

This topic felt very relevant because modern development often relies on dozens — if not hundreds — of third-party libraries. As a student, I’ve been guilty of “npm installing” a tool and forgetting about it. But seeing how a single outdated component led to the Equifax breach makes it clear: **every dependency is part of your attack surface**. If you're not watching them, no one is.

## Conclusion / Closing

Vulnerable and outdated components are a silent threat. They often go unnoticed until it's too late — even when patches exist. Keeping software up to date, monitoring advisories, and using automated tools to manage dependencies is essential to maintaining a secure application stack.

## References / ChatGPT Analysis

This report was drafted using **ChatGPT 4.0** for structure and refinement, and formatted with **GitHub Copilot in VS Code**. Source material was cross-verified with trusted cybersecurity reports and official documentation.

**References:**

- [OWASP Top 10: Vulnerable and Outdated Components](https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/)
- [OWASP Dependency-Check](https://owasp.org/www-project-dependency-check/)
- [U.S. House Oversight Report – Equifax](https://oversight.house.gov/wp-content/uploads/2018/12/Equifax-Report.pdf)
- [CVE-2017-5638](https://nvd.nist.gov/vuln/detail/CVE-2017-5638)
