### Descripción
Play this short game to get familiar with terminal applications and some of the most important rules in scope for picoCTF.Connect to the program with netcat:`$ nc verbal-sleep.picoctf.net 64240`

Hints:
1. When a choice is presented like [a/b/c], choose one, for example: `c` and then press Enter.

### Solución
Al iniciar el servidor en Webshell nos muestra un juego con una introducción y nos da varias opciones:

```
Options:
A) *Register multiple accounts*
B) *Share an account with a friend*
C) *Register a single, private account*
[a/b/c] > a
```

Y después nos deja iniciar el juego:
```
Options:
A) *Play the game*
B) *Search the Ether for the flag*
[a/b] > a

"Good choice, Ei," Nyx says, "You never want to share flags or artifact
downloads."

---
(Press Enter to continue...)
---

 Playing the Game
Playing the Game: 100%|██████████████████████████████████████ [time left: 00:00]
Playing the Game completed successfully!
```

Después de dar enter varias veces nos muestra lo siguiente:
```
END OF FANTASY CTF SIMULATION
Thank you for playing! To reemphasize some rules for this year:
1. Register only one account.
2. Do not share accounts, flags or artifact downloads.
3. Wait to publish writeups publicly until after the organizers announce the
winners.
4. picoCTF{m1113n1um_3d1710n_d5787049} is a real flag! Submit it for some
points in picoCTF 2025!
```

Y finaliza el juego.

Flag:
picoCTF{m1113n1um_3d1710n_d5787049}

### Notas adicionales


### Referencias
