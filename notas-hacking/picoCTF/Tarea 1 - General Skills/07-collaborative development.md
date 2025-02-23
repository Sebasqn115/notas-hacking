### Descripción
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/179/challenge.zip)

Hints:
1. `git branch -a` will let you see available branches
2. How can file 'diffs' be brought to the main branch? Don't forget to `git config`!
3. Merge conflicts can be tricky! Try a text editor like nano, emacs, or vim.

### Solución
Con Webshell

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/179/challenge.zip
--2025-02-23 05:46:57--  https://artifacts.picoctf.net/c_titan/179/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.42, 3.160.5.18, 3.160.5.93, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.42|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24648 (24K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                     100%[==========================================================>]  24.07K  --.-KB/s    in 0.01s   

2025-02-23 05:46:58 (2.26 MB/s) - 'challenge.zip' saved [24648/24648]

Sebas115-picoctf@webshell:~$ ls
challenge.zip
Sebas115-picoctf@webshell:~$ unzip challenge.zip

Sebas115-picoctf@webshell:~$ ls
challenge.zip  drop-in
Sebas115-picoctf@webshell:~$ cd drop-in/
Sebas115-picoctf@webshell:~/drop-in$ ls
flag.py
Sebas115-picoctf@webshell:~/drop-in$ cat flag.py 
print("Printing the flag...")
Sebas115-picoctf@webshell:~/drop-in$ python3 flag.py 
Printing the flag...
Sebas115-picoctf@webshell:~/drop-in$ nano flag.py

Sebas115-picoctf@webshell:~/drop-in$ git branch -a
Sebas115-picoctf@webshell:~/drop-in$ git checkout feature/part-1
Switched to branch 'feature/part-1'
Sebas115-picoctf@webshell:~/drop-in$ ls
flag.py
Sebas115-picoctf@webshell:~/drop-in$ cat flag.py 
print("Printing the flag...")
print("picoCTF{t3@mw0rk_", end='')

Sebas115-picoctf@webshell:~/drop-in$ git checkout feature/part-2
Switched to branch 'feature/part-2'
Sebas115-picoctf@webshell:~/drop-in$ python3 flag.py 
Printing the flag...
m@k3s_th3_dr3@m_

Sebas115-picoctf@webshell:~/drop-in$ git checkout feature/part-3
Switched to branch 'feature/part-3'
Sebas115-picoctf@webshell:~/drop-in$ python3 flag.py 
Printing the flag...
w0rk_798f9981}

```

picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_798f9981}

### Notas adicionales


### Referencias
https://webshell.picoctf.org/


