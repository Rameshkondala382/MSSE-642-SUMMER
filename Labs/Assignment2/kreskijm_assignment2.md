#### [🔙 Back to README](../../README.md)

# MSSE642 Assignment 2: Threat Modeling

## Part 1: Secure Design Document Overview

### 1. Project Description (Hiking Club Application)
The Hiking Club Application is a mission-critical web-based platform developed for the Georgia Hiking Club, a nonprofit organization coordinating hiking events locally and internationally. The application facilitates event management, user registrations, member profile handling, and secure payment processing. Designed for varying fitness levels, it prioritizes user-friendliness while enforcing robust data security measures for sensitive information, such as medical records and payment details.

### 2. Organization Description
The Georgia Hiking Club operates entirely through volunteer management, without a physical office space. It is overseen remotely by club officers, including a Chief Technology Officer (CTO), and funded through sponsorships and annual member fees. Members range widely in fitness levels, and hikes are rated to match member capabilities.

### 3. Deployment Environment
The Hiking Club application will be deployed specifically using Amazon Web Services (AWS) to ensure scalability, reliability, and security:

- **DNS & CDN:** Amazon Route 53 for DNS management and CloudFront for content distribution and caching, providing improved latency, security, and availability.
- **Frontend Web Server:** Hosted on Amazon EC2 within a public subnet. Traffic is managed by an Application Load Balancer (ALB), secured by AWS Web Application Firewall (WAF), and AWS Certificate Manager (ACM) for HTTPS traffic.
- **Backend Database Server:** Amazon RDS hosted within a private subnet, restricting access exclusively to the Frontend Server via Security Groups. Encryption at rest and in transit is enforced through AWS Key Management Service (KMS).
- **Authentication and Authorization:** Managed using AWS Cognito, enforcing OAuth 2.0 standards, Multi-Factor Authentication (MFA), and Role-Based Access Control (RBAC).
- **Administrative Access:** Admin endpoints are protected via AWS Client VPN, requiring secure, encrypted connections.
- **Monitoring and Logging:** AWS CloudWatch and AWS CloudTrail provide centralized log aggregation, monitoring, and alerts for security events and system anomalies.
- **Security Measures:** Include AWS Shield for DDoS protection, AWS Inspector for automated vulnerability scanning, and AWS Config for compliance auditing.

### 4. Secure Software Concepts

- **Authentication:** Strengthened with MFA and complex password enforcement.
- **Authorization:** RBAC enforced through AWS Cognito and IAM policies.
- **Data Confidentiality:** Comprehensive encryption of sensitive data at rest and in transit using AWS KMS.
- **Input Validation:** Robust data sanitization and validation to mitigate injection threats.
- **Audit Logging:** Detailed logging of user and system activities through AWS CloudTrail.
- **Availability:** Enhanced through CDN caching, load balancing, and AWS Shield protection.

---

## Part 2: Hiking Club Threat Model Assessment

### Part 2A: AWS Architectural Components

[Hiking Club Drawio Code](hikingclub.drawio)

[Hiking Club Diagram](hikingclub.png)

**Components:**
- Amazon Route 53 (DNS)
- Amazon CloudFront (CDN)
- AWS WAF
- AWS Application Load Balancer (ALB)
- Frontend Web Server (EC2, public IP)
- AWS Cognito (authentication)
- Backend Database Server (RDS, private IP)
- AWS Client VPN (admin access)
- AWS CloudWatch (monitoring/logging)
- AWS KMS (encryption)
- AWS Shield (DDoS protection)

**Networks:**
- Public Subnet (Frontend Web Server, ALB)
- Private Subnet (Backend Database Server)

**Firewall and Security:**
- AWS Security Groups (firewall rules)
- AWS Network ACLs

**Data Flows:**
- HTTPS traffic from users → Route 53 → CloudFront CDN → ALB → EC2
- Internal API calls from EC2 → RDS (private subnet)
- Admin VPN connections directly to internal services

**Trust Boundaries:**
- Public Network (untrusted)
- Private Network (trusted, internal AWS VPC)

### Part 2B: STRIDE Threat Model

- **Spoofing:** Mitigated with AWS Cognito and enforced MFA.
- **Tampering:** Reduced by implementing WAF rules and security group restrictions.
- **Repudiation:** Managed through comprehensive logging via CloudTrail and CloudWatch.
- **Information Disclosure:** Prevented by using encryption (AWS KMS) and restricted internal data access.
- **Denial of Service (DoS):** Protected by AWS Shield and load balancing via ALB and CloudFront CDN.
- **Elevation of Privilege:** Controlled by strong RBAC enforced through AWS IAM policies and AWS Cognito.

### Part 2C: OWASP Threat Model

**Assessment Scope:**
1. Member medical data, financial records
2. User authentication, authorization, and profile management
3. Administrative endpoints and backend database interactions

**Vulnerabilities:**
1. Potential weak authentication if improperly configured
2. Unprotected admin interfaces
3. SQL Injection through improperly validated inputs
4. Misconfigured AWS security settings leading to unauthorized access

**Countermeasures:**
1. Enforce strong authentication (AWS Cognito, MFA)
2. Input validation and sanitization at every layer
3. Regular security auditing (AWS Inspector, CloudWatch)
4. Strict RBAC and firewall settings (Security Groups and WAF)

**Prioritized Risks:**
1. Unauthorized access to confidential medical data (high)
2. User account compromise via weak authentication (high)
3. Exposure of administrative functions (medium)
4. Injection attacks on application forms (medium)
5. Logging misconfiguration leading to accountability issues (low)

---

## References

- [OWASP Top Ten](https://owasp.org/www-project-top-ten/)
- [OWASP Threat Modeling Guide](https://owasp.org/www-community/Application_Threat_Modeling)
- [OWASP Wiki on Threat Modeling](https://wiki.owasp.org/index.php/Category:Threat_Modeling)
- [EdrawMax: AWS Architecture Diagram Examples](https://www.edrawmax.com/article/aws-architecture-diagram-examples.html)
- [Gliffy: AWS Architecture Diagram Examples](https://www.gliffy.com/blog/aws-architecture-diagram-examples)
- [Creately: AWS VPC Architecture Diagram with Public and Private Subnets](https://creately.com/guides/aws-architecture-diagrams-and-use-cases/#aws-vpc-architecture-diagram-with-public-and-private-subnets)

