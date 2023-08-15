Run this command to convert it to pdf:
```sh
pandoc -s index.md -o index.pdf --pdf-engine=xelatex --toc -N --highlight-style my.theme
```