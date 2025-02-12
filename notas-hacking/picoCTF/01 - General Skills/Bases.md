### Descripción
What does this `bDNhcm5fdGgzX3IwcDM1` mean? I think it has something to do with bases.

**Hints:**
1. Submit your answer in our flag format. For example, if your answer was 'hello', you would submit 'picoCTF{hello}' as the flag.
### Solución
Con Webshell

'''
`Sebas115-picoctf@webshell:~$ echo "bDNhcm5fdGgzX3IwcDM1" | base64 --decode`
`l3arn_th3_r0p35Sebas115-picoctf@webshell:~$`
'''

**Solución 2**
Usando cyberchef https://gchq.github.io/CyberChef

'''
`Input: bDNhcm5fdGgzX3IwcDM1
`Recipe: From Base64`
`Output: l3arn_th3_r0p35`
'''

### Notas adicionales

### Referencias
https://webshell.picoctf.org/
https://gchq.github.io/CyberChef