### Descripción
I accidentally wrote the flag down. Good thing I deleted it!You download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/137/challenge.zip)

Hints:
1. Version control can help you recover files if you change or lose them!
2. Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control)
3. You can 'checkout' commits to see the files inside them

### Solución
Con Webshell

```
Sebas115-picoctf@webshell:~/drop-in$ wget https://artifacts.picoctf.net/c_titan/137/challenge.zip
--2025-02-23 05:29:59--  https://artifacts.picoctf.net/c_titan/137/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.42, 3.160.5.71, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19197 (19K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                     100%[==========================================================>]  18.75K  --.-KB/s    in 0.008s  

2025-02-23 05:29:59 (2.41 MB/s) - 'challenge.zip' saved [19197/19197]

Sebas115-picoctf@webshell:~/drop-in$ LS
-bash: LS: command not found
Sebas115-picoctf@webshell:~/drop-in$ ls
challenge.zip
Sebas115-picoctf@webshell:~/drop-in$ unzip challenge.zip 

Sebas115-picoctf@webshell:~/drop-in$ ls
challenge.zip  drop-in
Sebas115-picoctf@webshell:~/drop-in$ cd drop-in/
Sebas115-picoctf@webshell:~/drop-in/drop-in$ ls
message.txt
Sebas115-picoctf@webshell:~/drop-in/drop-in$ cat message.txt 
TOP SECRET
Sebas115-picoctf@webshell:~/drop-in/drop-in$ git log

Sebas115-picoctf@webshell:~/drop-in/drop-in$ git checkout ea859bf3b5d94ee74ce5ee1afa3edd7d4d6b35f0
Note: switching to 'ea859bf3b5d94ee74ce5ee1afa3edd7d4d6b35f0'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at ea859bf create flag
Sebas115-picoctf@webshell:~/drop-in/drop-in$ cat message.txt 
picoCTF{s@n1t1z3_cf09a485}

```

Al hacer el git log sale un commit en el que se creo la bandera y se toma ese para hacer un git checkout para crearla y al hacer el cat ahora si sale la bandera.

picoCTF{s@n1t1z3_cf09a485}

### Notas adicionales


### Referencias
https://webshell.picoctf.org/





