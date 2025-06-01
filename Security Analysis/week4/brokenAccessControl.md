# Broken Access Control

## Introduction & Description

Broken Access Control occurs when a system fails to properly enforce restrictions on what authenticated or unauthenticated users can access or modify. It often results from missing or misconfigured authorization checks and can lead to privilege escalation, unauthorized data exposure, or even full system compromise.

**Example:** A URL like `/admin/deleteUser?id=1234` can be accessed by any logged-in user instead of just admins. If the backend does not verify user roles properly, anyone could delete any user account.

More at: [OWASP A01:2021 - Broken Access Control](https://owasp.org/Top10/A01_2021-Broken_Access_Control/)

## Specific Real-World Example

One of the most well-known cases of Broken Access Control occurred with Snapchat in 2014, when hackers exploited a vulnerability in Snapchat's public API. The flaw existed in the app’s “Find Friends” feature, which allowed users to upload their phone contacts to find matches on the platform. However, Snapchat failed to implement proper rate limiting or authorization checks, allowing attackers to automate large-scale requests and harvest user data.

According to CNET, the attackers were able to match usernames with phone numbers for approximately 4.6 million accounts, which were later published online through a site called SnapchatDB.info (which was quickly taken down).

CNET reported that the hackers said they were attempting to raise awareness:

> “Our motivation behind the release was to raise the public awareness around the issue, and also put public pressure on Snapchat to get this exploit fixed.”

Notably, security researchers from Gibson Security had responsibly disclosed the vulnerability to Snapchat weeks before the breach, but it was reportedly not addressed in time.

Snapchat responded to the incident by releasing an update to its app that added the ability for users to opt out of being discovered by phone number. They also began implementing more robust request throttling. Despite the fix, the event was a clear example of how lax access control — particularly around public-facing APIs — can lead to massive data exposure.

**Sources:**
- [CNET: 4.6M Snapchat names and phone numbers leaked by hackers](https://www.cnet.com/tech/mobile/4-6m-snapchat-names-and-phone-numbers-leaked-by-hackers/)
- [TechCrunch: Hackers claim to publish list of 4.6M Snapchat usernames and numbers](https://techcrunch.com/2013/12/31/hackers-claim-to-publish-list-of-4-6m-snapchat-usernames-and-numbers/)
- [Gibson Security: Snapchat](https://gibsonsec.org/snapchat/)
- [Gibson Security: Full Disclosure](https://gibsonsec.org/snapchat/fulldisclosure/#the-find_friends-exploit)

## Analysis About How to Prevent

Preventing Broken Access Control involves several layered defenses:

- **Deny by default**: Block access unless explicitly permitted.
- **Enforce role-based access control (RBAC)** server-side.
- **Avoid client-side authorization checks** — always validate roles and permissions on the backend.
- **Use unique user IDs**, not easily guessed IDs like `/user/1`.
- **Log access violations** and monitor regularly for anomalies.
- Implement **least privilege**: grant users only what they need.

Refer to: [OWASP Authorization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html)

## My Thoughts 

This topic really highlights how security isn't just about login forms or passwords — it's about constant, consistent validation throughout an application. It was interesting to see how often vulnerabilities stem from assumptions that “the user will only see what we show them,” instead of validating what they’re allowed to do. As a student, it’s a clear takeaway that authorization logic must live on the server, not just in the UI.

## Conclusion / Closing

Broken Access Control remains one of the most dangerous and common vulnerabilities in modern web applications. Without strict enforcement of permissions at every level, systems can be exploited even by low-privilege users. Designing with secure defaults and rigorous backend checks is essential to protect against unauthorized actions.

## References / ChatGPT Analysis

This report was researched and compiled using verified sources, with assistance from **ChatGPT 4.0** to structure and refine the text. Markdown formatting and layout were improved using **GitHub Copilot in VS Code**. Sources were cross-verified through *OWASP*, *TechCrunch*, and *Gibson Security*.

**References:**
- [OWASP Top 10: Broken Access Control. (2021)](https://owasp.org/Top10/A01_2021-Broken_Access_Control/)
- [OWASP Authorization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html)
- [CNET: 4.6M Snapchat names and phone numbers leaked by hackers. (2014)](https://www.cnet.com/tech/mobile/)
- [TechCrunch: Snapchat Hack. (2013)](https://techcrunch.com/2013/12/31/hackers-claim-to-publish-list-of-4-6m-snapchat-usernames-and-numbers/)
- [Gibson Security: Full Disclosure. (2013)](https://gibsonsec.org/snapchat/fulldisclosure/)
- [Gibson Security: Snapchat. (2013)](https://gibsonsec.org/snapchat/)

