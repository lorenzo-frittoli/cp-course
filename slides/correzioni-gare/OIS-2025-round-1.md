# Competitive Programming (CP)
Correzione OIS 2025 Round 1

---

## Risorse
Tutto il materiale del corso puo' essere trovato su https://github.com/lorenzo-frittoli/cp-course
![[static/repo_qrcode.png|250]]

---

## Parkour (`parkour`)
La soluzione piu' semplice e' generare una griglia del tipo:
```txt
.....
#....
.#...
..#..
...#.
```
Questo chiaramente **non e' possibile** se abbiamo $M < N$.

---

### Implementazione

```py
level = [['.' for _ in range(M)] for i in range(N)]

if (M < N):
    print(-1)
    exit()

for i in range(1, N):
    level[i][i-1] = '#'


for i in range(N):
    for j in range(M):
        print(level[i][j], end="")
    print()
```

---


