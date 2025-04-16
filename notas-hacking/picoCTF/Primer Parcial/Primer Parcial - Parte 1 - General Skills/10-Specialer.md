### Descripción
Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer.`ssh -p 52463 ctf-player@saturn.picoctf.net`. The password is `8a707622`

Hints:
1. What programs do you have access to?

### Solución
Entramos al servidor personalizado del shell e introducimos la contraseña:

```
Sebas115-picoctf@webshell:~$ ssh -p 52463 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:52463 ([13.59.203.175]:52463)' can't be established.
ED25519 key fingerprint is SHA256:lMXKIC17ONzyUJx7ZYBY5VSwoxCz20uq5/Nm+IhXKew.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:52463' (ED25519) to the list of known hosts.
ctf-player@saturn.picoctf.net's password:
```

Buscamos ayuda con los comandos:
```
Specialer$ help
GNU bash, version 5.0.17(1)-release (x86_64-pc-linux-gnu)
These shell commands are defined internally.  Type `help' to see this list.
Type `help name' to find out more about the function `name'.
Use `info bash' to find out more about the shell in general.
Use `man -k' or `info' to find out more about commands not in this list.

A star (*) next to a name means that the command is disabled.

 job_spec [&]                                                      history [-c] [-d offset] [n] or history -anrw [filename] or hi>
 (( expression ))                                                  if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMANDS; ].>
 . filename [arguments]                                            jobs [-lnprs] [jobspec ...] or jobs -x command [args]
 :                                                                 kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or >
 [ arg... ]                                                        let arg [arg ...]
 [[ expression ]]                                                  local [option] name[=value] ...
 alias [-p] [name[=value] ... ]                                    logout [n]
 bg [job_spec ...]                                                 mapfile [-d delim] [-n count] [-O origin] [-s count] [-t] [-u >
 bind [-lpsvPSVX] [-m keymap] [-f filename] [-q name] [-u name] >  popd [-n] [+N | -N]
 break [n]                                                         printf [-v var] format [arguments]
 builtin [shell-builtin [arg ...]]                                 pushd [-n] [+N | -N | dir]
 caller [expr]                                                     pwd [-LP]
 case WORD in [PATTERN [| PATTERN]...) COMMANDS ;;]... esac        read [-ers] [-a array] [-d delim] [-i text] [-n nchars] [-N nc>
 cd [-L|[-P [-e]] [-@]] [dir]                                      readarray [-d delim] [-n count] [-O origin] [-s count] [-t] [->
 command [-pVv] command [arg ...]                                  readonly [-aAf] [name[=value] ...] or readonly -p
 compgen [-abcdefgjksuv] [-o option] [-A action] [-G globpat] [->  return [n]
 complete [-abcdefgjksuv] [-pr] [-DEI] [-o option] [-A action] [>  select NAME [in WORDS ... ;] do COMMANDS; done
 compopt [-o|+o option] [-DEI] [name ...]                          set [-abefhkmnptuvxBCHP] [-o option-name] [--] [arg ...]
 continue [n]                                                      shift [n]
 coproc [NAME] command [redirections]                              shopt [-pqsu] [-o] [optname ...]
 declare [-aAfFgilnrtux] [-p] [name[=value] ...]                   source filename [arguments]
 dirs [-clpv] [+N] [-N]                                            suspend [-f]
 disown [-h] [-ar] [jobspec ... | pid ...]                         test [expr]
 echo [-neE] [arg ...]                                             time [-p] pipeline
 enable [-a] [-dnps] [-f filename] [name ...]                      times
 eval [arg ...]                                                    trap [-lp] [[arg] signal_spec ...]
 exec [-cl] [-a name] [command [arguments ...]] [redirection ...>  true
 exit [n]                                                          type [-afptP] name [name ...]
 export [-fn] [name[=value] ...] or export -p                      typeset [-aAfFgilnrtux] [-p] name[=value] ...
 false                                                             ulimit [-SHabcdefiklmnpqrstuvxPT] [limit]
 fc [-e ename] [-lnr] [first] [last] or fc -s [pat=rep] [command>  umask [-p] [-S] [mode]
 fg [job_spec]                                                     unalias [-a] name [name ...]
 for NAME [in WORDS ... ] ; do COMMANDS; done                      unset [-f] [-v] [-n] [name ...]
 for (( exp1; exp2; exp3 )); do COMMANDS; done                     until COMMANDS; do COMMANDS; done
 function name { COMMANDS ; } or name () { COMMANDS ; }            variables - Names and meanings of some shell variables
 getopts optstring name [arg]                                      wait [-fn] [id ...]
 hash [-lr] [-p pathname] [-dt] [name ...]                         while COMMANDS; do COMMANDS; done
 help [-dms] [pattern ...]                                         { COMMANDS ; }
```

Inspeccionamos el sistema y el contenido de los directorios para ver los archivos ocultos e ir intentando leer cada uno hasta conseguir la bandera:
```
Specialer$ echo *
abra ala sim
Specialer$ echo .* *
. .. .hushlogin .profile abra ala sim
Specialer$ echo .* */*
. .. .hushlogin .profile abra/cadabra.txt abra/cadaniel.txt ala/kazam.txt ala/mode.txt sim/city.txt sim/salabim.txt
Specialer$ echo .* */* */.*
. .. .hushlogin .profile abra/cadabra.txt abra/cadaniel.txt ala/kazam.txt ala/mode.txt sim/city.txt sim/salabim.txt abra/. abra/.. ala/. ala/.. sim/. sim/..
Specialer$ echo .* */*
. .. .hushlogin .profile abra/cadabra.txt abra/cadaniel.txt ala/kazam.txt ala/mode.txt sim/city.txt sim/salabim.txt
Specialer$ echo "$(<abra/cadabra.txt)"
Nothing up my sleeve!
Specialer$ echo "$(<abra/cadaniel.txt)"
Yes, I did it! I really did it! I'm a true wizard!

Specialer$ echo "$(<ala/kazam.txt)"
return 0 picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_49193632}
```

### Notas adicionales


### Referencias
https://webshell.picoctf.org/
https://jarv.org/posts/cat-without-cat/