### Descripción
Connect to this PostgreSQL server and find the flag!`psql -h saturn.picoctf.net -p 57345 -U postgres pico`Password is `postgres`

Hints:
1. What does a SQL database contain?

### Solución
Entramos al servidor y observamos los comandos con \h:

```
┌──(kali㉿kali)-[~/picoCTF/parcial1/SQLDirect]
└─$ psql -h saturn.picoctf.net -p 57345 -U postgres pico
Password for user postgres: 
psql (17.0 (Debian 17.0-1+b2), server 15.2 (Debian 15.2-1.pgdg110+1))
Type "help" for help.

pico=# \h
```

Observamos que hay y hacemos un select a las banderas:
```
pico=# \dt
         List of relations
 Schema | Name  | Type  |  Owner   
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)

pico=# select * from flags;
 id | firstname | lastname  |                address                 
----+-----------+-----------+----------------------------------------
  1 | Luke      | Skywalker | picoCTF{L3arN_S0m3_5qL_t0d4Y_21c94904}
  2 | Leia      | Organa    | Alderaan
  3 | Han       | Solo      | Corellia
(3 rows)
```

Flag:
picoCTF{L3arN_S0m3_5qL_t0d4Y_21c94904}
### Notas adicionales

### Referencias
