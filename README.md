# ecommerce-sysdesign-pci
This is the architectural diagram that shows the system design on cloud that fulfills the PCI requirements on the ecommerce site.

![design](/images/sys_design.png)
Format: ![Alt Text](url)

## High-level solution of the architecture
* Cloudflare’s Web Application Firewall (WAF) with rules to mitigate the OWASP web app vulnerabilities.
* Elastic Load Balancing (ELB) for distribution of incoming application traffic across the EC2 instances.
* Access and privilege is strictly controlled using AWS Identity and Access Management (IAM) while data encrypted at rest and in motion using AWS Key Management Service (KMS).
* Application, infrastructure and monitoring logs that are generated are transferred to Splunk’s SIEM tool for centralized monitoring and event handling. 
* Amazon S3 for centralized logging, db backups, utilizing lifecycle policies for archiving objects in S3 Glacier, which supports PCI-compliant retention policies.
* Cloudwatch monitors the resources and applications. 
* Managed network address translation (NAT) gateways to allow outbound internet access for resources in the private subnet.
* A secured bastion login host to facilitate the command-line secure shell (SSH) access to EC2 instances for troubleshooting and system administration activities. These users are managed by LDAP.
* Standard security groups for EC2 and database instances.
* User defined database credentials.
