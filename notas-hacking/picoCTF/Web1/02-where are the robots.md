### Descripción
Can you find the robots? `https://jupiter.challenges.picoctf.org/problem/60915/` ([link](https://jupiter.challenges.picoctf.org/problem/60915/)) or http://jupiter.challenges.picoctf.org:60915

Hints:
1. What part of the website could tell you where the creator doesn't want you to look?

### Solución
La palabra robots nos indica que hay que buscar los rastreadores por lo que hay que cambiar el url de la página agregando robots.txt y está página nos manda:
User-agent: *
Disallow: /8028f.html

Ahora a la página inicial le agregamos la extensión que nos muestra /8028f.html y está página nos muestra lo siguiente:
Guess you found the robots  
picoCTF{ca1cu1at1ng_Mach1n3s_8028f}

Aquí ya se nos da la flag completa:
picoCTF{ca1cu1at1ng_Mach1n3s_8028f}

### Notas adicionales


### Referencias
https://jupiter.challenges.picoctf.org/problem/60915/
https://jupiter.challenges.picoctf.org/problem/60915/robots.txt
https://jupiter.challenges.picoctf.org/problem/60915/8028f.html