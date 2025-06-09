#### [🔙 Back to README](../../README.md)

# Security Logging and Monitoring Failures

## Introduction & Description

Security logging and monitoring failures occur when an application or system does not adequately record, retain, or review critical security-related events. This can lead to delayed breach detection, unnoticed attacks, or the inability to investigate incidents. Common causes include:

- No logging of authentication or access control events
- Logs missing critical details (e.g., IPs, timestamps)
- No alerting on suspicious or abnormal behavior
- Logging only on the client side, not the server

**Example:** An attacker performs 10,000 failed login attempts, but the system logs only the last attempt, and no alerts are raised. Without comprehensive logging and automated monitoring, security teams remain unaware of the brute-force attack.

More at: [OWASP A09:2021 – Security Logging and Monitoring Failures](https://owasp.org/Top10/A09_2021-Security_Logging_and_Monitoring_Failures/)

### Specific Real-World Example: Equifax Data Breach (2017)

The 2017 **Equifax** breach is a widely cited case of **security logging and monitoring failure**. Attackers exploited an unpatched Apache Struts vulnerability, gaining access to sensitive records including Social Security numbers, birthdates, and addresses for approximately 147 million people.

Despite the initial breach occurring in May 2017, **Equifax did not detect the unauthorized access for 76 days**. This delay was due in part to a failed monitoring system: the SSL certificate used by a device responsible for inspecting network traffic had expired and was not renewed for over a year.

According to the official [U.S. House Oversight Committee report](https://oversight.house.gov/wp-content/uploads/2018/12/Equifax-Report.pdf):

> “Attackers sent 9,000 queries on these 48 databases, successfully locating unencrypted personally identifiable information (PII) data 265 times. The attackers transferred this data out of the Equifax environment, unbeknownst to Equifax. Equifax did not see the data exfiltration because the device used to monitor ACIS network traffic had been inactive for 19 months due to an expired security certificate. On July 29, 2017, Equifax updated the expired certificate and immediately noticed suspicious web traffic.”

This highlights a critical failure: Equifax had monitoring infrastructure in place, but it was rendered useless by an expired certificate — a preventable oversight. Without proper alerts and certificate management, the breach went undetected, resulting in one of the largest data compromises in U.S. history.


## Analysis About How to Prevent

To prevent logging and monitoring failures:

- **Centralize logging** with tools like ELK, Splunk, or AWS CloudWatch
- **Log authentication events**, access control changes, and sensitive data access
- **Set up alerts** for suspicious activity (e.g., multiple failed logins, privilege changes)
- **Retain logs** in secure, tamper-proof storage
- **Monitor logs in real time** and ensure incident response teams review them regularly
- Ensure **monitoring tools are not disabled** due to expired certificates or misconfigurations

Refer to: [OWASP Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html)

## My Thoughts

This topic reminded me how security isn’t just about preventing attacks — it’s also about detecting and reacting to them. The Equifax case showed how something as simple as an expired certificate can blind a company’s visibility into its own network. As someone learning more about cybersecurity, it’s a good reminder that even perfect firewalls and encryption won’t help if you can’t tell when something’s wrong.

## Conclusion / Closing

Logging and monitoring failures leave organizations blind to ongoing attacks and vulnerable to delayed breach responses. Implementing centralized, real-time, and well-structured logging with automated alerting is a critical part of modern defense. Without visibility, there is no security.

## References / ChatGPT Analysis

This report was researched using verified sources and structured with the help of **ChatGPT 4.0** for clarity. Markdown formatting and layout were assisted by **GitHub Copilot in VS Code**. All external facts were cross-checked against public reports and documentation.

**References:**

- [OWASP Top 10: Security Logging and Monitoring Failures](https://owasp.org/Top10/A09_2021-Security_Logging_and_Monitoring_Failures/)
- [OWASP Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html)
- [U.S. House Report on Equifax Breach (PDF)](https://oversight.house.gov/wp-content/uploads/2018/12/Equifax-Report.pdf)
- [The Verge – Equifax Breach](https://www.theverge.com/2017/9/22/16345580/equifax-data-breach-credit-identity-theft-updates)

