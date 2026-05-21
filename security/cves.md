# CVEs





### Dataset Construction

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
