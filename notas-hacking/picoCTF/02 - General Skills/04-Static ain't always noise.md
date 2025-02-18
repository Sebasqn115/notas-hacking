### Descripción
Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/ec4dbd8898ade34e1d60d5b70c1b8c8c/static)? This [BASH script](https://mercury.picoctf.net/static/ec4dbd8898ade34e1d60d5b70c1b8c8c/ltdis.sh) might help!

### Solución
Con Python

```
Sebas115-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/ec4dbd8898ade34e1d60d5b70c1b8c8c/static
--2025-02-18 18:28:38--  https://mercury.picoctf.net/static/ec4dbd8898ade34e1d60d5b70c1b8c8c/static
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8376 (8.2K) [application/octet-stream]
Saving to: 'static'

static                         100%[====================================================>]   8.18K  --.-KB/s    in 0s      

2025-02-18 18:28:38 (305 MB/s) - 'static' saved [8376/8376]

Sebas115-picoctf@webshell:~$ file static
static: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=639391a8b15c579d69659462d3c935fa61693f17, not stripped
Sebas115-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/ec4dbd8898ade34e1d60d5b70c1b8c8c/ltdis.sh
--2025-02-18 18:29:17--  https://mercury.picoctf.net/static/ec4dbd8898ade34e1d60d5b70c1b8c8c/ltdis.sh
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 785 [application/octet-stream]
Saving to: 'ltdis.sh'

ltdis.sh                       100%[====================================================>]     785  --.-KB/s    in 0s      

2025-02-18 18:29:17 (757 MB/s) - 'ltdis.sh' saved [785/785]

Sebas115-picoctf@webshell:~$ file ltdis.sh 
ltdis.sh: Bourne-Again shell script, ASCII text executable
Sebas115-picoctf@webshell:~$ ls
big-zip-files  ltdis.sh  static
Sebas115-picoctf@webshell:~$ chmod +x static
Sebas115-picoctf@webshell:~$ ./static
Oh hai! Wait what? A flag? Yes, it's around here somewhere!
Sebas115-picoctf@webshell:~$ bash ltdis.sh 
Attempting disassembly of  ...
objdump: 'a.out': No such file
objdump: section '.text' mentioned in a -j option, but not found in any input file
Disassembly failed!
Usage: ltdis.sh <program-file>
Bye!
Sebas115-picoctf@webshell:~$ bash ltdis.sh static
Attempting disassembly of static ...
Disassembly successful! Available at: static.ltdis.x86_64.txt
Ripping strings from binary with file offsets...
Any strings found in static have been written to static.ltdis.strings.txt with file offset
Sebas115-picoctf@webshell:~$ ls 
big-zip-files  ltdis.sh  static  static.ltdis.strings.txt  static.ltdis.x86_64.txt
Sebas115-picoctf@webshell:~$ nano ltdis.sh 
Sebas115-picoctf@webshell:~$ static static.ltdis.strings.txt 
-bash: static: command not found
Sebas115-picoctf@webshell:~$ cat static.ltdis.strings.txt 
    238 /lib64/ld-linux-x86-64.so.2
    361 libc.so.6
    36b puts
    370 __cxa_finalize
    37f __libc_start_main
    391 GLIBC_2.2.5
    39d _ITM_deregisterTMCloneTable
    3b9 __gmon_start__
    3c8 _ITM_registerTMCloneTable
    660 AWAVI
    667 AUATL
    6ba []A\A]A^A_
    6e8 Oh hai! Wait what? A flag? Yes, it's around here somewhere!
    7c7 ;*3$"
   1020 picoCTF{d15a5m_t34s3r_98d35619}
   1040 GCC: (Ubuntu 7.5.0-3ubuntu1~18.04) 7.5.0
   1671 crtstuff.c
   167c deregister_tm_clones
   1691 __do_global_dtors_aux
   16a7 completed.7698
   16b6 __do_global_dtors_aux_fini_array_entry
   16dd frame_dummy
   16e9 __frame_dummy_init_array_entry
   1708 static.c
   1711 __FRAME_END__
   171f __init_array_end
   1730 _DYNAMIC
   1739 __init_array_start
   174c __GNU_EH_FRAME_HDR
   175f _GLOBAL_OFFSET_TABLE_
   1775 __libc_csu_fini
   1785 _ITM_deregisterTMCloneTable
   17a1 puts@@GLIBC_2.2.5
   17b3 _edata
   17ba __libc_start_main@@GLIBC_2.2.5
   17d9 __data_start
   17e6 __gmon_start__
   17f5 __dso_handle
   1802 _IO_stdin_used
   1811 __libc_csu_init
   1821 __bss_start
   182d main
   1832 __TMC_END__
   183e _ITM_registerTMCloneTable
   1858 flag
   185d __cxa_finalize@@GLIBC_2.2.5
   187a .symtab
   1882 .strtab
   188a .shstrtab
   1894 .interp
   189c .note.ABI-tag
   18aa .note.gnu.build-id
   18bd .gnu.hash
   18c7 .dynsym
   18cf .dynstr
   18d7 .gnu.version
   18e4 .gnu.version_r
   18f3 .rela.dyn
   18fd .rela.plt
   1907 .init
   190d .plt.got
   1916 .text
   191c .fini
   1922 .rodata
   192a .eh_frame_hdr
   1938 .eh_frame
   1942 .init_array
   194e .fini_array
   195a .dynamic
   1963 .data
   1969 .bss
   196e .comment
Sebas115-picoctf@webshell:~$ cat static.ltdis.strings.txt | grep pico
   1020 picoCTF{d15a5m_t34s3r_98d35619}

```


Otra alternativa es usar el comando strings static | grep pico:

```
Sebas115-picoctf@webshell:~$ strings static | grep pico
picoCTF{d15a5m_t34s3r_98d35619}
```

picoCTF{d15a5m_t34s3r_98d35619}

### Notas adicionales


### Referencias
https://webshell.picoctf.org/
