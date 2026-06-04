# CVEs

## Automatic CVE Container Scanning Pipeline



* **Trivy**: best overall for ease of use and broad coverage.
* **Syft + Grype**: great if you want SBOM-first workflows and a modular setup.
* **Clair**: solid if you want a more registry-centric scanner.
* **GitLab container scanning**: useful if your pipeline already lives in GitLab.





```
podman run docker.io/aquasec/trivy
```

<br>





### Dataset Construction



* **100% free core sources:** MITRE CVE, NVD, OSV, Exploit-DB
* **Free + developer-friendly APIs:** GitHub Advisories, OSV

#### Core global CVE systems

* MITRE CVE Program\
  The official source of CVE IDs (like CVE-2024-xxxx). It defines vulnerabilities but does not provide rich exploit details.\
  [https://www.cve.org/](https://www.cve.org/)
* NIST National Vulnerability Database\
  The most widely used enriched CVE database. Adds severity scores (CVSS), references, and analysis.\
  [https://nvd.nist.gov/](https://nvd.nist.gov/)

***

#### Developer-focused vulnerability databases

* GitHub Security Advisories\
  Large database of vulnerabilities affecting open-source packages (npm, PyPI, RubyGems, etc.).\
  [https://github.com/advisories](https://github.com/advisories)
* Open Source Vulnerabilities (OSV)\
  Designed for modern package ecosystems and used heavily in dependency scanning.\
  [https://osv.dev/](https://osv.dev/)

#### Exploit-focused databases

* Exploit Database\
  Focuses on proof-of-concept exploits and working attack code rather than just CVEs.\
  [https://www.exploit-db.com/](https://www.exploit-db.com/)







Merge:

1. GitHub Advisory DB
2. OSV
3. NVD
4. Supply-chain incident datasets
5. Malware-package feeds

Normalize by:

* Package name
* CVE ID
* Publication date
* Severity
* CWE
* Ecosystem
* Attack type



## Best Overall Combination

If I were building this dataset today:

| Purpose                    | Best Source                |
| -------------------------- | -------------------------- |
| CVE metadata               | GitHub Advisory DB         |
| Severity                   | NVD                        |
| npm vulnerability coverage | OSV                        |
| Malicious packages         | Socket + Phylum            |
| Dependency graphs          | deps.dev                   |
| Incident reports           | CISA + security journalism |
