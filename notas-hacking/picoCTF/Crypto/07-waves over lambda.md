### Descripción
We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with `nc jupiter.challenges.picoctf.org 39894`.

Hints:
1. Flag is not in the usual flag format

### Solución
Nos conectamos al puerto indicado.
Observamos un texto cifrado por sustitución.
Utilizamos una herramienta para decodificar el texto cifrado:
```
`Input: vgbwjtif peje nf lgkj outw - ojezkebvl_nf_v_gyej_utqcst_twouvwilke
-------------------------------------------------------------------------------
ptynbw pts fgqe inqe ti ql snfrgftu xpeb nb ugbsgb, n pts ynfnies ipe cjninfp qkfekq, tbs qtse fetjvp tqgbw ipe cggdf tbs qtrf nb ipe uncjtjl jewtjsnbw ijtbfluytbnt; ni pts fijkvd qe ipti fgqe ogjedbgxueswe go ipe vgkbijl vgkus ptjsul otnu ig ptye fgqe nqrgjitbve nb setunbw xnip t bgcueqtb go ipti vgkbijl. n onbs ipti ipe snfijnvi pe btqes nf nb ipe ehijeqe etfi go ipe vgkbijl, mkfi gb ipe cgjsejf go ipjee fitief, ijtbfluytbnt, qgustynt tbs ckdgynbt, nb ipe qnsfi go ipe vtjrtipntb qgkbitnbf; gbe go ipe xnusefi tbs uetfi dbgxb rgjingbf go ekjgre. n xtf bgi tcue ig unwpi gb tbl qtr gj xgjd wnynbw ipe ehtvi ugvtunil go ipe vtfiue sjtvkut, tf ipeje tje bg qtrf go ipnf vgkbijl tf lei ig vgqrtje xnip gkj gxb gjsbtbve fkjyel qtrf; cki n ogkbs ipti cnfijnia, ipe rgfi igxb btqes cl vgkbi sjtvkut, nf t otnjul xeuu-dbgxb rutve. n fptuu ebiej peje fgqe go ql bgief, tf ipel qtl jeojefp ql qeqgjl xpeb n itud gyej ql ijtyeuf xnip qnbt.`
`Language: English`
`Output: congrats here is your flag - frequency_is_c_over_lambda_agflcgtyue`
```
La bandera no se encuentra en el formato que normalmente tenemos, hay que ponerla tal cual nos la da.

Flag:
frequency_is_c_over_lambda_agflcgtyue
### Notas adicionales
Cifrado por Sustitución: un cifrado por sustitución es un método de cifrado en el que se reemplazan unidades de texto plano con el texto cifrado , de forma definida, mediante una clave. Las "unidades" pueden ser letras individuales (la más común), pares de letras, tripletes de letras, combinaciones de las anteriores, etc. El receptor descifra el texto realizando el proceso de sustitución inversa para extraer el mensaje original.

### Referencias
https://en.wikipedia.org/wiki/Substitution_cipher
Herramienta para decodificar por sustitución:
https://www.guballa.de/substitution-solver