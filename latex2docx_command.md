### Latex to word powershell command 

```shell
cd "C:\Users\bryan\OneDrive\Documents\papers\crop2cloud"; pandoc -s main.tex --citeproc --bibliography=references.bib -o main.docx
```

### Print diff btw 2 files powershell command:
```shell
git diff --no-index old_main.tex main.tex | Out-File -FilePath diff.txt -Encoding utf8 
```
