### Descripción
What was I last working on? I remember writing a note to help me remember...You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/66/challenge.zip)

Hints:
1. The `cat` command will let you read a file, but that won't help you here!
2. Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control).
3. When committing a file with git, a message can (and should) be included.

### Solución
Con Webshell

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/66/challenge.zip
--2025-02-23 05:34:56--  https://artifacts.picoctf.net/c_titan/66/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.71, 3.160.5.93, 3.160.5.42, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.71|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17740 (17K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                     100%[==========================================================>]  17.32K  --.-KB/s    in 0.001s  

2025-02-23 05:34:56 (23.8 MB/s) - 'challenge.zip' saved [17740/17740]

Sebas115-picoctf@webshell:~$ ls
challenge.zip
Sebas115-picoctf@webshell:~$ unzip challenge.zip

Sebas115-picoctf@webshell:~$ ls
challenge.zip  drop-in
Sebas115-picoctf@webshell:~$ cd drop-in/
Sebas115-picoctf@webshell:~/drop-in$ ls
message.txt
Sebas115-picoctf@webshell:~/drop-in$ cat message.txt 
This is what I was working on, but I'd need to look at my commit history to know why...Sebas115-picoctf@webshell:~/drop-in$ git log
Sebas115-picoctf@webshell:~/drop-in$ git log
Sebas115-picoctf@webshell:~/drop-in$ 
Sebas115-picoctf@webshell:~/drop-in$ git checkout 3339c144a0c78dc2fbd3403d2fb37d3830be5d94
Note: switching to '3339c144a0c78dc2fbd3403d2fb37d3830be5d94'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 3339c14 picoCTF{t1m3m@ch1n3_d3161c0f}

```


picoCTF{t1m3m@ch1n3_d3161c0f}

### Notas adicionales


### Referencias
https://webshell.picoctf.org/





