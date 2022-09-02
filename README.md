# Application security FAQ
A FAQ on secure application development and acquisition
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
### Where can I find static analysis tools?
(not tested)
- [Codacy](https://www.codacy.com) (github/gitlab code scanner)
- [Android application pentesting guide](https://nightowl131.github.io/AAPG/)
- [PHPstan](https://github.com/phpstan/phpstan) - PHP static analyzer
- [Psalm](https://psalm.dev/docs/running_psalm/installation/) (PHP static analyzer)

### Where/how can I generate an SBOM (software bill of materials)?
- [Syft](https://github.com/anchore/syft) - A tool for generating the SBOM from container images and filesystems

## TEST
#### How can I test for authentication?
(not tested)
- [Blazy](https://github.com/s0md3v/Blazy) - bruteforcer
- [Burp extensions](https://github.com/snoopysecurity/awesome-burp-extensions) - a curated list of Burp extensions

## How can I test against man-in-the-middle attacks?
- [Maproxy](https://pypi.org/project/maproxy/) - TCP injection proxy

## OPS
### How to scan my workloads for configuration errors or weaknesses?
- [Prowler](https://github.com/prowler-cloud/prowler) - Detect configuration errors and weaknesses in AWS workloads
- [Trivy](https://github.com/aquasecurity/trivy) - Detects vulnerabilities and hard-coded secrets in container images, git repos
 
### How to scan code repositories for hard-coded secrets?
- [SSHGit](https://github.com/eth0izzle/shhgit/) - Detect hard-coded secrets in code repositories

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
