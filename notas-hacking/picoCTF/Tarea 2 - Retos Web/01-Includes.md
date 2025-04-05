### Descripción
Can you get the flag?
Go to this [website](http://saturn.picoctf.net:62043/) and see what you can discover.

Hints:
1. Is there more code than what the inspector initially shows?
### Solución
Se inspecciona la página que se nos da y en el archivo style.css se encuentra documentada la primer parte de la flag:

```
body {
  background-color: lightblue;
}

/*  picoCTF{1nclu51v17y_1of2_  */

```

Después, en el script.js se encuentra la segunda y ultima parte de la flag:
```



function greetings()
{
  alert("This code is in a separate file!");
}

//  f7w_2of2_df589022}

```

Flag:
picoCTF{1nclu51v17y_1of2_f7w_2of2_df589022}

### Notas adicionales


### Referencias

