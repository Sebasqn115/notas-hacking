### Descripción
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz).

Hints:
1. Cargo is Rust's package manager and will make your life easier. See the getting started page [here](https://doc.rust-lang.org/book/ch01-03-hello-cargo.html)
2. [println!](https://doc.rust-lang.org/std/macro.println.html)
3. Rust has some pretty great compiler error messages. Read them maybe?

### Solución
Descargar el archivo y ver las carpetas: 
```
┌──(kali㉿kali)-[~/picoCTF/parcial1]
└─$ wget https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz
--2025-04-15 16:26:39--  https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 65.9.149.95, 65.9.149.85, 65.9.149.59, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|65.9.149.95|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1415 (1.4K) [application/octet-stream]
Saving to: ‘fixme1.tar.gz’

fixme1.tar.gz           100%[==============================>]   1.38K  --.-KB/s    in 0s      

2025-04-15 16:26:40 (74.1 MB/s) - ‘fixme1.tar.gz’ saved [1415/1415]

                                                                                               
┌──(kali㉿kali)-[~/picoCTF/parcial1]
└─$ tar -xvzf fixme1.tar.gz 
fixme1/
fixme1/Cargo.toml
fixme1/Cargo.lock
fixme1/src/
fixme1/src/main.rs
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/parcial1]
└─$ cd fixme1
```

Aplicar un cargo build:
```
──(kali㉿kali)-[~/picoCTF/parcial1/fixme1]
└─$ cargo build
    Updating crates.io index
  Downloaded crossbeam-deque v0.8.5
  Downloaded xor_cryptor v1.2.3
  Downloaded either v1.13.0
  Downloaded crossbeam-utils v0.8.20
  Downloaded crossbeam-epoch v0.9.18
  Downloaded rayon-core v1.12.1
  Downloaded rayon v1.10.0
  Downloaded 7 crates (388.2 KB) in 1.59s
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling either v1.13.0
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/home/kali/picoCTF/parcial1/fixme1)
error: expected ;, found keyword let
 --> src/main.rs:5:37
  |
5 |     let key = String::from("CSUCKS") // How do we end statements in Rust?
  |                                     ^ help: add ; here
...
8 |     let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", ...
  |     --- unexpected token

error: argument never used
  --> src/main.rs:26:9
   |
25 |         ":?", // How do we print out a variable in the println function? 
   |         ---- formatting specifier missing
26 |         String::from_utf8_lossy(&decrypted_buffer)
   |         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ argument never used

error[E0425]: cannot find value ret in this scope
  --> src/main.rs:18:9
   |
18 |         ret; // How do we return in rust?
   |         ^^^ help: a local variable with a similar name exists: res

For more information about this error, try rustc --explain E0425.
error: could not compile rust_proj (bin "rust_proj") due to 3 previous errors
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/parcial1/fixme1]
└─$ ls
Cargo.lock  Cargo.toml  src  target
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/parcial1/fixme1]
└─$ cd src     
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/parcial1/fixme1/src]
└─$ ls
main.rs
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/parcial1/fixme1/src]
└─$ nano main.rs 
```

Pero aquí hay algunos errores que se solucionan entrando al archivo con nano y corrigiendo lo necesario. Solo se agregaron cosas que faltaban para completar algunas líneas.
Después volver a realizar el cargo build y correrlo:
```
┌──(kali㉿kali)-[~/picoCTF/parcial1/fixme1/src]
└─$ cargo build
   Compiling rust_proj v0.1.0 (/home/kali/picoCTF/parcial1/fixme1)
    Finished dev profile [unoptimized + debuginfo] target(s) in 0.66s
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/parcial1/fixme1/src]
└─$ ls         
main.rs
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/parcial1/fixme1/src]
└─$ cargo run  
    Finished dev profile [unoptimized + debuginfo] target(s) in 0.10s
     Running /home/kali/picoCTF/parcial1/fixme1/target/debug/rust_proj
picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}:?
```

Flag:
picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}
### Notas adicionales

### Referencias
