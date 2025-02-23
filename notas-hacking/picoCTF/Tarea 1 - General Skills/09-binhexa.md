### Descripción
How well can you perfom basic binary operations?
Start searching for the flag here `nc titan.picoctf.net 58957`

### Solución
Con Webshell y usando una calculadora binaria https://www.ecalculator.co/calc/es/calculadora-binaria

```
Sebas115-picoctf@webshell:~$ nc titan.picoctf.net 58957

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 11110110
Binary Number 2: 01110100


Question 1/6:
Operation 1: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 0b110111101111000
Correct!

Question 2/6:
Operation 2: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 0b111101100
Correct!

Question 3/6:
Operation 3: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 0b11110110
Correct!

Question 4/6:
Operation 4: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 0b1110100
Correct!

Question 5/6:
Operation 5: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 0b101101010
Correct!

Question 6/6:
Operation 6: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 0b111010
Correct!

Enter the results of the last operation in hexadecimal: 0x3a

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_6ab1ad84}

```


picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_6ab1ad84}

Usando cyberchef https://gchq.github.io/CyberChef

```
`Input: 111010`
`Recipe: From Binary To Hex`
`Output: 3a`
```
### Notas adicionales


### Referencias
https://webshell.picoctf.org/
https://www.ecalculator.co/calc/es/calculadora-binaria
https://gchq.github.io/CyberChef
