# Starbuck's cybersecurity FAQ
A FAQ on stuff related to cybersecurity

## Where to start...
### ...on devsecops?
- [DevSecOps: Implement security on CICD Pipeline](https://medium.com/@DevOps-Diva.o/devsecops-implement-security-on-cicd-pipeline-19eb7aa22626) - One of the best introduction articles on the topic of devsecops, by Devsecops Diva

## How to evaluate a Vendor?
- [Vendor questionnaire](https://docs.google.com/document/d/1idP1gGuEgeinoL6m_hsZ8lQ8wz64BeI-S53n_9kwMkU) at Mozilla
- [Vendor questionnaire](https://github.com/google/vsaq) at Google
## DESIGN
### What fundamental principles should I follow?
- [NIST SP800-160: Systems Security Engineering](https://csrc.nist.gov/publications/detail/sp/800-160/vol-1/final) - nist.gov
- Principles (subset):
  - Least Privilege (deny by default)
  - Defense in depth
  - Minimized sharing
  - Trusted components
  - Trusted communication channels
  - Trusted input
  - Secure defaults
  - Accountability and traceability
  - Secure failure and recovery
  - Acceptable security
  - Human factored security
  - Repeatable security

## BUILD
### Where can I find coding guidelines?
- [Django secure coding](https://dzone.com/articles/protect-your-django-web-application-from-security-1) - Dzone.com
- [Django secure coding](https://docs.djangoproject.com/en/2.1/topics/security/) - Djangoproject.com
- 
### Where/how can I generate an SBOM (software bill of materials)?
- [Syft](https://github.com/anchore/syft) - A tool for generating the SBOM from container images and filesystems

## VERIFY
### How do I test an authentication mechanism?
(not tested)
- [Blazy](https://github.com/s0md3v/Blazy) - bruteforcer
- [Burp extensions](https://github.com/snoopysecurity/awesome-burp-extensions) - a curated list of Burp extensions

### How can I test against man-in-the-middle attacks?
- [Maproxy](https://pypi.org/project/maproxy/) - TCP injection proxy

### How do I test my apps for vulnerabilities?
- [Android application pentesting guide](https://nightowl131.github.io/AAPG/)
- [Chopchop](https://github.com/michelin/ChopChop) - Web application security scanner

### How do I check my code for vulnerabilities and errors? (SAST tools)
- [Bandit](https://github.com/PyCQA/bandit) - SAST for Python
- [Codacy](https://www.codacy.com) - SAST in Github & Gitlab
- [PHPstan](https://github.com/phpstan/phpstan) - SAST for PHP
- [Psalm](https://psalm.dev/docs/running_psalm/installation/) - SAST for PHP
- [Semgrep](https://semgrep.dev/) - SAST for many languages


### How do I verify my code dependencies are secure?
- [Dependabot](https://docs.github.com/en/code-security/dependabot/working-with-dependabot) - Dependency checker integrated in GitHub
- [Safety](https://pypi.org/project/safety/) - Dependency checker for Python

### How to verify everything is configured securely?
- [ADOscanner](https://github.com/azsk/ADOScanner-docs) - Detects vulnerabilities in an Azure devops instance
- [AzTS](https://github.com/azsk/AzTS-docs) - Azure tenant scanner, detects configuration vulnerabilities in an Azure tenant
- [Checkov](https://www.checkov.io/) - Detects vulnerabilities in IaC code (e.g. Terraform)
- [Clair](https://github.com/quay/clair) - Detects vulnerabilities in container images
- [CloudCustodian](https://cloudcustodian.io/) - Scans cloud platforms for policy violations (policies can be defined as YAML files)
- [Cloudsplaining](https://github.com/salesforce/cloudsplaining) - Detects IAM flaws in AWS
- [Cloudsploit](https://github.com/aquasecurity/cloudsploit) - Detects configuration issues in public clouds
- [CloudQuery](https://github.com/quarkslab/kdigger) - Cloud data integration platform (includes security policies as baseline)
- [CloudTracker](https://github.com/duo-labs/cloudtracker) - Detects over-privileged accounts in AWS
- [Dockle](https://github.com/goodwithtech/dockle) - Detects vulnerabilities in docker images
- [Hadolint](https://github.com/hadolint/hadolint) - Detects vulnerabilities in DOCKERFILE files
- [KDigger](https://github.com/quarkslab/kdigger) - Detects vulnerabilities in Kubernetes instances
- [KubeLinter](https://github.com/stackrox/kube-linter) - Detects flaws in Kubernetes YAML files and Helm charts
- [Lunar](https://github.com/lateralblast/lunar) - Detects configuration errors or weaknesses in operating systems (host scan)
- [Prowler](https://github.com/prowler-cloud/prowler) - Detect configuration errors and weaknesses in AWS workloads
- [ROADTools](https://github.com/dirkjanm/ROADtools) - Builds a queriable set of meta-data about an Azure AD instance
- [Scout suite](https://github.com/nccgroup/ScoutSuite) - Detects configuration errors in cloud control planes
- [SkyArk](https://github.com/cyberark/SkyArk) - Detects shadow admins in AWS and Azure
- [Terrascan](https://terrasolid.com/products/terrascan/) - Detects configuration weaknesses and errors in Terraform code
- [Tfsec](https://github.com/aquasecurity/tfsec) - Detects config weaknesses and errors in Terraform code
- [Trivy](https://github.com/aquasecurity/trivy) - Detects vulnerabilities and hard-coded secrets in container images, git repos
 
### How to scan code repositories for hard-coded secrets?
- [SSHGit](https://github.com/eth0izzle/shhgit/) - Detect hard-coded secrets in code repositories

## OPS

### How do I generate SBOMs? 
- [Kubeclarity](https://github.com/openclarity/kubeclarity) - Produces SBOMs and scans for vulnerabilities in container images

### How do I generate inventories of my resources? (cloud)
- [AWS Inventory](https://github.com/nccgroup/aws-inventory) - Generates an queriable inventory of resources in AWS account

### Are there tools to help me respond to an incident?
- [The Hive](https://thehive-project.org/) - Case management
- [Timesketch](https://github.com/google/timesketch) - Timeline visualization

## Web technology 
### Cookies
#### How should I secure my cookies?
Sensitive cookies (e.g. session cookie) should be protected *at least* with the following attributes:
- 'secure' --> forces transmission over HTTPS only.
- 'httpOnly' --> prevents interactive access from local JavaScript.
- 'expires' --> defines an automatic expiration date.
- 'domain' --> restricts the domains, and in particular, subdomains, to which it can be transmitted.
- 'path' --> restricts the Urls to which the cookie will be sent. Important when multiple apps are running on the same server.
- 'samesite' --> defines whether the cookie will be included in cross-site requests.

### Local storage
#### Is localStorage / sessionStorage secure?
Access to localStorage/sessionStorage objects is filtered per origin, similar to a SOP. Only code running from the same origin itself can access the content of the local storage. If "secure" meant "protected from XSS attacks", the answer is no: local storage can be manipulated when under a successful XSS attack. As a principle, storage of confidential/sensitive data in localStorage/sessionStorage should be avoided.

## Cloud stuff
### Cloud workload security checklists / guidance
- [Cloudsec Docs](https://cloudsecdocs.com/)

### Container hardening / checklists
- [Kubernetes security checklist](https://kubernetes.io/docs/concepts/security/security-checklist/)

## Other stuff
### How to show things? (data vizualisation)
- [VivaGraphJS](https://github.com/anvaka/VivaGraphJS) : a library to visualize graphs / connected stuff.

### How to convince the pesimistic crowd?
(not tested)
- [LinuxFlaw](https://github.com/VulnReproduction/LinuxFlaw): a repo of reproduced Linux vulnerabilities

### Someday stuff
(not tested)
- [ASN1 Javascript parser](http://lapo.it/asn1js/): a visual parser of DER/CER encoded strings
