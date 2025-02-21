### Descripción
Run the Python script and convert the given number from decimal to binary to get the flag.[Download Python script](https://artifacts.picoctf.net/c/24/convertme.py)

Hints:
1. Look up a decimal to binary number conversion app on the web or use your computer's calculator!
2. The `str_xor` function does not need to be reverse engineered for this challenge.
3. If you have Python on your computer, you can download the script normally and run it. Otherwise, use the `wget` command in the webshell.
4. To use `wget` in the webshell, first right click on the download link and select 'Copy Link' or 'Copy Link Address'
5. Type everything after the dollar sign in the webshell: `$ wget` , then paste the link after the space after `wget` and press enter. This will download the script for you in the webshell so you can run it!
6. Finally, to run the script, type everything after the dollar sign and then press enter: `$ python3 convertme.py`

### Solución
Con Webshell

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/24/convertme.py
--2025-02-20 19:23:30--  https://artifacts.picoctf.net/c/24/convertme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.71, 3.160.5.93, 3.160.5.42, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.71|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1189 (1.2K) [application/octet-stream]
Saving to: 'convertme.py'

convertme.py                      100%[==========================================================>]   1.16K  --.-KB/s    in 0s      

2025-02-20 19:23:30 (446 MB/s) - 'convertme.py' saved [1189/1189]

Sebas115-picoctf@webshell:~$ ls                                             
convertme.py

Sebas115-picoctf@webshell:~$ python3 convertme.py 
If 81 is in decimal base, what is it in binary base?
Answer: 1010001
That is correct! Here's your flag: picoCTF{4ll_y0ur_b4535_722f6b39}

```

picoCTF{4ll_y0ur_b4535_722f6b39}

Usando cyberchef https://gchq.github.io/CyberChef

```
`Input: 81`
`Recipe: From Decimal To Binary`
`Output: 1010001`
```


### Notas adicionales


### Referencias
https://webshell.picoctf.org/
https://gchq.github.io/CyberChef


