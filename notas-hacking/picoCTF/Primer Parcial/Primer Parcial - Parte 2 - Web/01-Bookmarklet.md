### Descripción
Why search for the flag when I can make a bookmarklet to print it for me?Browse [here](http://titan.picoctf.net:64980/), and find the flag!

Hints:
1. A bookmarklet is a bookmark that runs JavaScript instead of loading a webpage.
2. What happens when you click a bookmarklet?
3. Web browsers have other ways to run JavaScript too.

### Solución
Al entrar a la página nos muestra lo siguiente:
```
## Welcome to my flag distribution website!

If you're reading this, your browser has succesfully received the flag.

Here's a bookmarklet for you to try:

        javascript:(function() {
            var encryptedFlag = "àÒÆÞ¦È¬ëÙ£ÖÓÚåÛÑ¢ÕÓÔÅÐÙí";
            var key = "picoctf";
            var decryptedFlag = "";
            for (var i = 0; i < encryptedFlag.length; i++) {
                decryptedFlag += String.fromCharCode((encryptedFlag.charCodeAt(i) - key.charCodeAt(i % key.length) + 256) % 256);
            }
            alert(decryptedFlag);
        })();
    
```

Tomamos el bookmarklet de javascript y nos vamos a inspeccionar la página y lo pegamos en la consola, lo cual hace que al ejecutarlo nos mande un mensaje que muestre lo siguiente:
```
titan.picoctf.net:64980 dice
picoCTF{p@g3_turn3r_1d1ba7e0}
```

Flag:
picoCTF{p@g3_turn3r_1d1ba7e0}
### Notas adicionales

### Referencias
