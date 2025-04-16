### Descripción
Cookie Monster has hidden his top-secret cookie recipe somewhere on his website. As an aspiring cookie detective, your mission is to uncover this delectable secret. Can you outsmart Cookie Monster and find the hidden recipe?You can access the Cookie Monster [here](http://verbal-sleep.picoctf.net:56241/) and good luck

Hints:
1. Sometimes, the most important information is hidden in plain sight. Have you checked all parts of the webpage?
2. Cookies aren't just for eating - they're also used in web technologies!
3. Web browsers often have tools that can help you inspect various aspects of a webpage, including things you can't see directly.

### Solución
Entrando a la página nos pide loguearnos. Al intentar entrar con cualquier usuario y contraseña nos deniega el acceso.
Al inspeccionar la página e irnos a las cookies encontramos una la cual se encuentra decodificada en base64.
Utilizamos CyberChef para decodificarla:

```
`Input: cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzXzZDMkZCN0YzfQ%3D%3D`
`Recipe: From Base64`
`Output: picoCTF{c00k1e_m0nster_l0ves_c00kies_6C2FB7F3}`
```

Flag:
picoCTF{c00k1e_m0nster_l0ves_c00kies_6C2FB7F3}
### Notas adicionales

### Referencias
https://gchq.github.io/CyberChef/