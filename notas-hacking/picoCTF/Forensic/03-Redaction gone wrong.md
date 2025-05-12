### Descripción
Now you DON’T see me.This [report](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf) has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?

Hints:
1. How can you be sure of the redaction?

### Solución
Descargamos el archivo .pdf.
Al abrirlo observamos algunas palabras ocultas con un recuadro negro.
Podemos copiar todo el texto incluyendo esos recuadros y pegarlo en un bloc de notas para observar todo el contenido y aquí se nos revela la bandera.
```
Sebas115-picoctf@webshell:~/forensic$ wget https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf
--2025-05-12 06:50:27--  https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.16, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34915 (34K) [application/octet-stream]
Saving to: 'Financial_Report_for_ABC_Labs.pdf'

Financial_Report_for_ABC_Labs.pdf 100%[==========================================================>]  34.10K  --.-KB/s    in 0.01s   

2025-05-12 06:50:27 (3.18 MB/s) - 'Financial_Report_for_ABC_Labs.pdf' saved [34915/34915]

Financial Report for ABC Labs, Kigali, Rwanda for the year 2021.
Breakdown - Just painted over in MS word.

Cost Benefit Analysis
Credit Debit
This is not the flag, keep looking
Expenses from the
picoCTF{C4n_Y0u_S33_m3_fully}
Redacted document.
```


Flag:
picoCTF{C4n_Y0u_S33_m3_fully}
### Notas adicionales


### Referencias
