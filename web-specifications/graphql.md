# GraphQL

```json
query ($cursor: String) {
  securityAdvisories(first: 100, after: $cursor) {
    pageInfo {
      hasNextPage
      endCursor
    }
    nodes {
      ghsaId
      summary
      description
      severity
      publishedAt
      updatedAt
      withdrawnAt

      identifiers {
        type
        value
      }

      cvss {
        score
        vectorString
      }

      cwes(first: 10) {
        nodes {
          cweId
          name
        }
      }

      references {
        url
      }

      vulnerabilities(first: 20) {
        nodes {
          package {
            name
            ecosystem
          }
          vulnerableVersionRange
          firstPatchedVersion {
            identifier
          }
          severity
        }
      }
    }
  }
}
```
