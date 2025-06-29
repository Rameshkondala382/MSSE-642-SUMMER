# Ramesh KONDALA
# MSSE-642 Software Engineering Leadership
# JUNE-29, 2025
 





# Short Essay #1: General Security Concepts (250+ words)

Referencing Hoffman (Hoffman, Chapter 1) and the lecture and slides:
Define the following "General Security Concepts" in your own words:

**Confidentiality:**

It means sensitive information is accessible only to authorized members only. This is done through an access control system, encryption and authentication mechanism, which prevents unauthorized access from stealing or viewing data.


**Example:** 
Only specific professors have access to their classes, which prevents unauthorized access to enter and manipulate the course data, and multifactor authentication might be used to further restrict entry.
Breaches of confidentiality, such as data leaks, threats, and insider attacks, can expose personal data and trade secrets.


**Integrity:**
It refers to the accuracy, consistency, and trustworthiness of people or anything throughout its lifecycle. Data must not be altered, accessed, modified, deleted, or tampered with by unauthorized parties. Mechanisms such as digital signatures and version controls help ensure that information remains unchanged from its original state. Integrity is vital for decision-making as manipulated data can lead to worst outcomes or loss of trust from systems.

**Availability**.
It ensures information and resources are available to authorized users whenever needed. It means systems must be resilient against hardware failures, cyber-attacks and natural disasters. Backups and failover systems are used to maintain availability even the most secure and accurate data are useless if it cannot be accessed in a timely manner.

## Define the phases of software security from 1930 through the present day.

**1930s–1940s:** Cryptography and Early Hacking
Mechanical encryption was introduced to protect wartime communications. Figures like Marian Rejewski established the foundation of modern cryptanalysis and demonstrated the importance of confidentiality and integrity in secure communications.

**1950s–1960s:** Telephony and Phreaking
Automated telephone networks were raised. Phreakers exploited tone-based signaling to manipulate calls and evade billing. This era highlighted the risks of designing systems for best-case use

**1970s–1980s:** Computerization and Malware
Personal computers became famous, and the first viruses and worms appeared, such as the Morris worm. This period shifted from physical security to information security with a growing focus on integrity.

**1990s:** The Internet and Web Security
In this phase, the World Wide Web introduced new vulnerabilities. Attackers focused on web servers and applications and used protocols and software to attack. The need for confidentiality and integrity rose as e-commerce and online communication grew.

**2000s:** Cybercrime and Advanced Threats
Phishing and cross-site attacks rose in this phase. Security strategies evolved to include encryption and authentication as attackers targeted users and application logic.


**2010s–Present:** Cloud, Compliance, and Application Security
High profile breaches and regulatory requirements like GDPR came. Modern browser and protocols like SOP, SSL offered strong protections. The CIA is the guiding framework for protecting data and systems as technology and threat continue to evolve.















# Short Essay #2: TLS (250+ words)

**References:** 
 Lecture Recording and Slides
In your own words, briefly answer the following.  


**What are TLS certificates and how do they differ from SSL certificates (you can google this).**


TLS certificates serve as digital credentials that verify the identity of websites and facilitate secure communication between clients and servers. The terms SSL and TLS are frequently used interchangeably. Secure socket layer (SSL) was the original protocol for securing web traffic, but it depreciated due to security flaws. Transport layer security is the modern and more secure 

**What two things do TLS certificates do to improve security?**

**Authentication:**

When a browser connects to a website, the TLS certificate verifies the website is legitimate. This is done through a handshake process where the certificate is checked against trusted certificate authorities to confirm the website’s identity.

**Encryption:**
TLS certificates ensure it encrypts the data exchange between the server and the client. This involves sensitive information such as passwords, payment details, and personal details that cannot be accessible to read by malicious actors.



**What are some of the challenges involved in using TLS certificates?**
**Certificates have expiry dates;**

failure to renew them on time can lead to service outages and user trust.

Using outdated version protocols such as TLS 1 and 1.1 or any weaker suites can leave systems vulnerable to attacks.


Web owners should not compromise with certificate authorities; otherwise, they fall prey to fraudulent certificates issued by attackers.


Lack of security certificate management leads to expiry and creates security gaps.


Need to be very careful when allowing permissions should not give permissions accidentally to attackers.


**Referring to the challenges you listed in the previous part, what can be done to address these challenges?**

Automated tools to inventory, monitor, renew, and revoke certificates reduces the risk of outages.


Regular auding on systems to ensure they are using attest and secure TLS Versions.


Managing and assigning persons for certificate management.


Monitoring certificate configurations and status and CA activity to detect abnormalities.


Training the staff on how to use TLS and its configurations and management to improve overall security.















# Short Essay #3: Penetration Testing (3 paragraphs)

References:  Singh: Chap 1
Briefly answer the following in your own words.

**Of the four penetration testing methodologies, e.g. SANS 25, choose one and describe it in a paragraph. •:**

OSSTMM, which stands for the Open-Source Security Testing Methodology Manual, is a fantastic resource! This manual is community-driven, regularly updated, and peer-reviewed, making it a must-know set of security testing standards for every ethical hacker. It's designed to cover a wide range of testing topics, and it’s especially helpful for newcomers in the industry. By familiarizing themselves with these standards, they can gain a better understanding of the testing process and discover best practices to ensure their success.
The knowledge gained from OSSTMM will be an asset for a penetration tester. In the next section, we will discuss the benefits of also understanding SANS 25.

**Penetration Testing Approach: Black Box Testing**
Black box testing is a method of penetration testing and is the most common assessment of network penetration, where the tester has no prior knowledge of the internal workings, architecture, or networks of the target system. The tester interacts with the system as an external attacker and relies solely on publicly available information. This approach resembles a real-world attack scenario, as it requires the discovery of vulnerabilities without insider information. Black box testing is often more difficult and requires more time due to the need for thorough reconnaissance; however, it offers crucial insights into how external users may manipulate the system.

 **Of the six types of penetration tests, e.g. "Web Application Penetration Testing," choose one and describe it in a paragraph**
**Type of Penetration Test:** Web Application Penetration Testing
Web application penetration testing is all about discovering and addressing vulnerabilities in web applications. This exciting journey usually starts with information gathering, which can either be passive, making use of public sources, or active, where we interact directly with the application. Testers examine issues related to authentication, session management, input validation, API security, and other key areas. Common attack scenarios involve checking for SQL injection vulnerabilities, bypassing authentication methods, taking advantage of weak password reset processes, and assessing how predictable API tokens can be. The objective is to discover weaknesses that could enable unauthorized access, data leaks, or manipulation of application functionality, thereby assisting organizations in protecting their web applications from actual threats.















# Short Essay #4: Containers and security (250+ words)
**References:**  Rice: Chap 1.

**Of the 9 container security threats described in the reading, describe in your own words the three most significant.  What are these threats and why 
did you choose these?**

**Containers and Security:** The Three Most Significant Threats
The growth of containers has transformed software deployment by providing agility and scalability. Nonetheless, this transition has brought forth new security concerns. Among the nine container security threats discussed in Rice Chapter 1, the three most critical are supply chain attacks, container escape vulnerabilities, and inadequate secrets management.


**Supply chain attacks**
 represent one of the most serious risks to container security. Today’s containerized applications consist of various components, often obtained from public repositories and third-party vendors. If any segment of this supply chain is compromised—be it a base image, a dependency, or even the build pipeline itself—malicious code can infiltrate production environments. This threat is intensified by the automation and rapid pace of modern DevOps practices, where images are often pulled and deployed without thorough manual checks. A single compromised component can trigger a ripple effect, potentially affecting thousands of deployments. The challenge of detecting such tampering before containers reach production renders this threat particularly dangerous.


**Container escape vulnerabilities**Containers are a major concern. While they are built to isolate applications, they utilize the host’s operating system kernel. If an attacker takes advantage of a weakness in the container runtime, they may escape the isolation provided by the container and gain access to the host system. This situation not only endangers the compromised container but also all other containers operating on the same host. The implications can be severe, particularly in multi-tenant environments or when handling sensitive workloads. Notable incidents and the continued identification of runtime bugs underscore the ongoing risk of container escapes.


**Poor secrets management** is a third threat that is often overlooked. Containers usually require access to sensitive credentials, including API keys or database passwords. When these secrets are embedded in images, stored insecurely, or managed poorly, attackers who infiltrate a container or image registry can easily retrieve them. This poses a risk of unauthorized access to essential systems and potential data breaches. As organizations expand their container usage, the likelihood of unintentional secret exposure increases, particularly in the absence of strong, centralized secrets management solutions.

The three significant threats—supply chain attacks, container escape vulnerabilities, and ineffective secrets management—are notable as they leverage essential elements of container technology: reliance on external components, shared infrastructure, and the necessity for secure communication. If not adequately managed, each can lead to extensive harm, highlighting the critical need for layered security measures and ongoing vigilance within containerized settings.












# Long Essay (40/100 points total, 500+ words).

**Part 1**
**General Penetration Testing**

| Phase | Description | Tools |
|:-----------|:------------:|------------:|
| InformationGathering|  The information gathering phase is the crucial first step in penetration testing, focused on collecting valuable data about the target system, organization, or network. We use both passive and active techniques. Passive gathering involves collecting publicly available information without interacting directly with the target, such as exploring company websites, social media, and public databases to identify employee names, email addresses, and technologies. In contrast, active gathering engages with the target—like DNS interrogation or network scanning—to discover live hosts, services, and operating system details, essential for profiling and identifying vulnerabilities. The insights gained are vital for planning our next steps and identifying entry points.   | Harvestor   |
| Vulnerability Analysis| Vulnerability analysis is all about taking a thorough look at security weaknesses in a system or network and figuring out which ones need our attention most. Building on the insights gathered during the information-gathering stage, we use some handy tools to spot things like misconfigurations, outdated software, and vulnerabilities that haven’t been addressed yet. Our aim here is to understand just how serious each vulnerability is (think CVSS scores) and see which ones could be exploited. We leverage scanners that automatically compare system details with known databases of vulnerabilities, giving us some great insights that help us create focused defenses against potential attacks. | Nessus      |
|Exploitation| The exploitation phase is all about making the most of the vulnerabilities we've identified to sneak into or take charge of target systems. During this vital step, we check just how serious those vulnerabilities are by mimicking real-world attacks, often with proof-of-concept exploits. This involves a variety of techniques, like delivering payloads, slipping past authentication barriers, and gaining additional privileges. When we succeed in this phase, it gives us a solid starting point for exploring more within the network. |Metasploit Framework |








## Deep Dive:  Website Penetration Testing


| Phase|       Description | Tools |
|:-----------|:------------:|------------:|
| Website Penetration Testing:Information gathering|     The information gathering phase in website penetration testing focuses on collecting valuable insights about the target web application and its underlying infrastructure. This involves identifying the technologies in use (like server software, frameworks, and CMS platforms), mapping out all accessible URLs and endpoints, and discovering any other sites hosted on the same server. Testers utilize a mix of passive and active reconnaissance techniques—such as examining public records, analyzing HTTP headers, and deploying automated crawlers—to explore subdomains, directories, and application logic. The goal here is to create a thorough profile of the web application, revealing potential entry points and understanding its structure. This crucial step paves the way for a more targeted vulnerability assessment and exploitation.  | Example: Maltego   |
| Website Penetration Testing:Gaining Access| The gaining access phase focuses on exploiting vulnerabilities discovered during earlier stages to compromise the web application or its backend systems. Penetration testers attempt real-world attacks such as SQL injection, cross-site scripting (XSS), file upload vulnerabilities, and local file inclusion (LFI) to bypass authentication, execute arbitrary code, or extract sensitive data from the server. This phase often involves crafting custom payloads and leveraging automated tools to validate the exploitability of identified weaknesses. Successfully gaining access demonstrates the practical risk posed by vulnerabilities and provides insight into the potential impact of an attack on the web application and its users| Example: Burp Suite    |




# Part 2: Tool Description and Analysis

1.	**The Harvester**
Vendor Website: [https://github.com/laramies/theHarvester](https://)
**Description: 
**the Harvester is a passive tool that gathers information from public sources like search engines, PGP key servers, and social media, collecting emails, subdomains, hosts, and open ports. It automates workflows for Open-Source Intelligence (OSINT) to map out attack surfaces without raising any alarms. Its modular design also allows for integration with platforms like Shodan and Hunter.io, enabling broader data collection.

**Kali Linux 2019: Pre-installed.**
**Testing the Hiking Club Application:**
For the Hiking Club’s web application, the Harvester helps to identify useful subdomains (like `events.hikingclub.com`) and the employee emails associated with the organization. This valuable information supports phishing simulations and testing for potential vulnerabilities in login portals. By linking exposed infrastructure details to public job postings, testers can make educated guesses about backend technologies (such as WordPress) that are ripe for targeted vulnerability analysis.


2.	**Nessus**
Vendor Website: [https://www.tenable.com/products/nessus](https://)
**Description:**
Nessus is a great commercial vulnerability scanner that helps you identify misconfigurations, missing patches, and exploitable flaws in your networks, web apps, and cloud infrastructure. With the power of real-time threat intelligence, it prioritizes risks using CVSS scores and Enable’s VPR (Vulnerability Priority Rating) to keep you informed. Some of the standout features include credentialed scanning for more in-depth system audits and compliance checks against recognized frameworks like CIS.


**Kali Linux 2019: Requires manual installation.**
**Testing the Hiking Club Application:**
For the Hiking Club’s web server and network, Nessus would scan for vulnerabilities like outdated Apache versions or insecure SSL/TLS configurations. By examining the results, testers can assess SQL injection risks or unsecured API endpoints. The post-scan reports help guide remediation efforts, prioritizing critical flaws such as remote code execution (RCE) for patching first.

**3.Metasploit Framework**
Vendor Website: [https://www.metasploit.com](https://)
**Description:**
Metasploit is an open-source tool that helps with exploitation and has pre-built modules for delivering payloads, escalating privileges, and performing activities after a compromise. It can be integrated with Nmap and Nessus for targeted attacks and supports creating custom exploits. Its database keeps track of compromised hosts for simulations that involve lateral movement.


**Kali Linux 2019: Pre-installed.**
**Testing the Hiking Club Application:**
After detecting a vulnerable plugin (like outdated Joomla) using Nessus, Metasploit would launch a matching exploit to get a reverse shell. Testers would then move to internal databases, extracting user credentials or altering hike registration data to show the breach's impact.

4.	**Maltego**
Vendor Website: [https://www.maltego.com](https://)
**Description:**
Maltego uses OSINT data to visualize connections between entities like domains, IPs, and social profiles. It queries APIs from platforms like Shodan, WHOIS, and social media to create a map of an organization’s infrastructure. This tool is useful for assessing attack surfaces and pinpointing risks related to third-party vendors.


**Kali Linux 2019: Requires manual installation.**
**Testing the Hiking Club Application:**
Maltego would map out the Hiking Club’s digital presence, exposing linked cloud storage (like AWS S3 buckets) or partner sites (such as payment gateways). If S3 buckets are overexposed, they might leak member data, and if partner systems have misconfigured APIs, they could be used as entry points for cross-site attacks.

**5.	Burp Suite**
Vendor Website: [https://portswigger.net/burp](https://)
**Description:**
Burp Suite is a web app testing toolkit featuring an intercepting proxy, scanner, and intruder for manual/automated vulnerability detection. It identifies issues like XSS, CSRF, and insecure authentication mechanisms. The Community Edition is free, while Pro adds advanced scanning and CI/CD integration.


**Kali Linux 2019: Pre-installed (Community Edition)**
Testing the Hiking Club Application: Burp Suite would intercept HTTP requests from the club’s login form, testing for SQLi via payloads like. The scanner audits user profile pages for stored XSS vulnerabilities, where malicious scripts could hijack sessions. Fuzzing API endpoints with Intruder reveals insecure direct object references (IDOR) exposing member data
