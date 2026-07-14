# pdf



`pdfunite`



## Merge pdfs



```
#!/usr/bin/env bash
set -euo pipefail

cd "$HOME/Documents/pdfs"

# Natural version sort (handles 01, 02, 10, etc.)
mapfile -t files < <(ls -1v *.pdf)

# Merge into a single PDF in correct order
pdfunite "${files[@]}" merged.pdf

echo "Created: merged.pdf"

```
