### Descripción
Theres tapping coming in from the wires. What's it saying `nc jupiter.challenges.picoctf.org 48247`.

Hints:
1. What kind of encoding uses dashes and dots?
2. The flag is in the format PICOCTF{}

### Solución
Nos conectamos al puerto y servidor para observar que sucede.
Nos manda un código morse.
Utilizando Cyberchef para decodificar el código:
```
`Input: .--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. .---- ..--- -.... .---- ....- ...-- ---.. .---- ---.. .---- }`
`Recipe: From Morse Code`
`Output: PICOCTFM0RS3C0D31SFUN1261438181`
```
Finalmente, le damos el formato correcto a la bandera.

Flag:
picoCTF{M0RS3C0D31SFUN1261438181}
### Notas adicionales


### Referencias
https://gchq.github.io/CyberChef