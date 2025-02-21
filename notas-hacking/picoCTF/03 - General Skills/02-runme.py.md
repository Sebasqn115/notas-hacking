### Descripción
Run the `runme.py` script to get the flag. Download the script with your browser or with `wget` in the webshell.[Download runme.py Python script](https://artifacts.picoctf.net/c/34/runme.py)

Hints:
1. If you have Python on your computer, you can download the script normally and run it. Otherwise, use the `wget` command in the webshell.
2. To use `wget` in the webshell, first right click on the download link and select 'Copy Link' or 'Copy Link Address'
3. Type everything after the dollar sign in the webshell: `$ wget` , then paste the link after the space after `wget` and press enter. This will download the script for you in the webshell so you can run it!
4. Finally, to run the script, type everything after the dollar sign and then press enter: `$ python3 runme.py` You should have the flag now!

### Solución
Con Webshell

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/34/runme.py
--2025-02-20 19:13:29--  https://artifacts.picoctf.net/c/34/runme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.42, 3.160.5.18, 3.160.5.71, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.42|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 270 [application/octet-stream]
Saving to: 'runme.py'

runme.py                          100%[==========================================================>]     270  --.-KB/s    in 0s      

2025-02-20 19:13:29 (18.3 MB/s) - 'runme.py' saved [270/270]

Sebas115-picoctf@webshell:~$ ls
README.txt  runme.py

Sebas115-picoctf@webshell:~$ python3 runme.py 
picoCTF{run_s4n1ty_run}

```

picoCTF{run_s4n1ty_run}

O también haciendo un cat al archivo:

```
Sebas115-picoctf@webshell:~$ cat runme.py 
#!/usr/bin/python3
################################################################################
# Python script which just prints the flag
################################################################################

flag ='picoCTF{run_s4n1ty_run}'
print(flag)
```

### Notas adicionales


### Referencias
https://webshell.picoctf.org/

