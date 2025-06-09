#### [🔙 Back to README](../../README.md)


# Software and Data Integrity Failures

## Introduction & Description

Software and Data Integrity Failures occur when applications do not properly protect against unauthorized changes to code, configuration, or data. These issues often arise from:

- Unverified software updates
- Unsigned or tampered packages
- CI/CD pipeline vulnerabilities
- Insecure use of plugins or libraries

This type of failure can lead to widespread compromise if attackers manipulate dependencies or insert malicious code into trusted components — especially during automated build or deployment processes.

**Example:** If an application automatically pulls and runs code from an external source (e.g., NPM or PyPI) without validating its integrity, an attacker could publish a similarly named malicious package that is executed unknowingly by the system.

More at: [OWASP A08:2021 – Software and Data Integrity Failures](https://owasp.org/Top10/A08_2021-Software_and_Data_Integrity_Failures/)

### Specific Real-World Example: SolarWinds Supply Chain Attack (2019–2020)

One of the most impactful examples of a software and data integrity failure was the **SolarWinds Orion supply chain attack**, publicly disclosed in December 2020. This breach demonstrated how tampering with trusted software at the source level can silently infiltrate thousands of organizations — including major U.S. government agencies and Fortune 500 companies.

According to [CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa20-352a), nation-state threat actors compromised SolarWinds’ software development environment. They inserted a malicious backdoor — later named **SUNBURST** — into legitimate Orion software updates, which were then distributed to over 18,000 customers.

> “The APT actor used compromised SolarWinds Orion updates to gain access to victim networks and remained undetected for months.” — CISA

But the attack’s timeline began much earlier, as detailed in a [2021 NPR investigation](https://www.npr.org/2021/04/16/985439655/a-worst-nightmare-cyberattack-the-untold-story-of-the-solarwinds-hack). In September 2019, the attackers planted a **small test snippet** of code — a simple check for the system's processor type:

> “This little snippet of code doesn't do anything,” said security researcher Meyers. “It's literally just checking to see which processor is running on the computer [...] and returns either a zero or a one.”

This snippet served as a **proof of concept**, confirming the attackers could insert code into SolarWinds' build environment and see it propagate into a signed, downloadable release.

After confirming this access, the attackers went quiet for five months. When they returned in February 2020, they deployed an advanced malware implant that allowed them to modify Orion’s source code **before it was built and digitally signed**.

> “They began by implanting code that told them any time someone on the SolarWinds development team was getting ready to build new software,” NPR reported. They exploited the CI/CD process, monitoring when developers checked code out of version control — “sort of like checking a book out of the library.”

This manipulation of SolarWinds' software lifecycle — including bypassing the “digital factory seal” that would normally reveal tampering — enabled attackers to distribute malware as part of trusted updates. Victims unknowingly installed compromised software, granting attackers persistent access.

This attack demonstrated not only a catastrophic failure in software integrity protections, but also the ease with which trust in signed code can be abused when the build pipeline is compromised at its root.


## Analysis About How to Prevent

To prevent software and data integrity failures:

- **Digitally sign software, packages, and updates**
- **Verify signatures and checksums** before use in deployment
- **Use trusted sources** and pin package versions in dependency files
- **Secure your CI/CD pipeline**, including build agents and credentials
- Enable **dependency scanning** and monitor for tampered packages
- Enforce **access controls** on version control and release systems

Refer to: [OWASP Software Supply Chain Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Software_Supply_Chain_Security_Cheat_Sheet.html)

## My Thoughts

What stood out most in the SolarWinds case was not just that the attackers inserted malicious code — but **how early and subtly they began**. The idea that a simple test snippet could be quietly inserted months ahead of the real attack, just to test access, shows a level of patience and sophistication that's difficult to defend against.

As a student learning about software security, it’s clear that protecting code doesn’t stop at writing secure functions. You have to secure the entire build lifecycle — your source control, CI/CD pipelines, and even the people and processes behind them. The most dangerous exploits don’t always involve obvious flaws; sometimes, they involve **exploiting the trust built into the system itself**.

---

## Conclusion / Closing

Software and data integrity failures represent some of the most difficult threats to detect — and the most damaging when exploited. As the SolarWinds attack demonstrated, even digitally signed software can be compromised if attackers gain access to the build pipeline. Preventing these failures requires securing the full development and deployment process, not just the code.

Strong controls around version control access, CI/CD monitoring, and signature validation are essential. Without them, attackers can hijack trusted updates and distribute malware under the guise of legitimate software — bypassing many traditional defenses in the process.


## References / ChatGPT Analysis

This report was created using verified sources and supported by **ChatGPT 4.0** for drafting and refinement. **GitHub Copilot in VS Code** was used to assist with formatting and structure. Facts were validated using CISA, OWASP, and public analysis of the SolarWinds breach.

**References:**

- [OWASP Top 10: Software and Data Integrity Failures](https://owasp.org/Top10/A08_2021-Software_and_Data_Integrity_Failures/)
- [OWASP Software Supply Chain Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Software_Supply_Chain_Security_Cheat_Sheet.html)
- [CISA - "Advanced Persistent Threat Compromise of Government Agencies, Critical Infrastructure, and Private Sector Organizations"](https://www.cisa.gov/news-events/cybersecurity-advisories/aa20-352a)
- [NPR - "A 'Worst Nightmare' Cyberattack: The Untold Story Of The SolarWinds Hack"](https://www.npr.org/2021/04/16/985439655/a-worst-nightmare-cyberattack-the-untold-story-of-the-solarwinds-hack)

