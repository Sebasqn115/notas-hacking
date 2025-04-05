### Descripción
Do you know how to use the web inspector?Start searching [here](http://titan.picoctf.net:50162/) to find the flag

Hints:
1. Use the web inspector on other files included by the web page.
2. The flag may or may not be encoded
### Solución
En la sección de about dentro de la página web: http://titan.picoctf.net:63007/about.html al inspeccionar esta parte se observa un conjunto de caracteres que pueden ser una pista: 

```
cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMjgzZTYyZmV9
```

Estos se pasan a CyberChef en Base64 para convertir y obtener la bandera:
```
`Input: cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMjgzZTYyZmV9`
`Recipe: From Base64`
`Output: picoCTF{web_succ3ssfully_d3c0ded_283e62fe}`
```

Flag:
picoCTF{web_succ3ssfully_d3c0ded_283e62fe}

### Notas adicionales


### Referencias
CyberChef: https://gchq.github.io/CyberChef/
