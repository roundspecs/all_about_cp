Run this command to convert it to pdf:
```sh
pandoc -s index.md -o index.pdf --pdf-engine=weasyprint --toc -N --webtex
```