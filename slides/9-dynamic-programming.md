# Competitive Programming (CP)
Lezione 9: Dynamic Programming

---

## Risorse
Tutto il materiale del corso puo' essere trovato su https://github.com/lorenzo-frittoli/cp-course
![[static/repo_qrcode.png|250]]

---

## Recursione
Serie di Fibonacci
```py
def fibonacci(x):
    if (x == 0 or x == 1):
        return 1
    return fibonacci(x-2) + fibonacci(x-1)
```

---

## Complessita'
$$O(2^N)$$
```
        --4--
       /     \
      3       2
     / \     / \
    2   1   1   0
   / \
  1   0
```

---

## Ottimizzazione
Quando calcolo `fib(N)` calcolo `fib(N-1)` e `fib(N-2)`.

Ma quando calcolo `fib(N-1)` calcolo di nuovo `fib(N-2)`, e cosi via.

Possiamo evitare di ricalcolare ste cose come dei babbosauri **salvando** i **risultati intermedii**.

Questa tecnica e' detta *memoizzazione* o *memoization*.

---

## Implementazione
```py
N_MAX = 1000
dp = [-1 for _ in range(N_MAX)]
dp[0] = 1
dp[1] = 1

def fibonacci(x):
    if (dp[x] != -1):
        return dp[x]
    dp[x] = fibonacci(x-2) + fibonacci(x-1)
    return dp[x]
```

---

## "Ottimizzazione"
Di solito e' piu' facile utilizzare una soluzione *iterativa* invece che una *recorsiva*.

Ed e' anche un po' piu' performante, ma non granche'.

---

## Implementazione
```py
x = 10

dp = [-1 for _ in range(x)]
dp[0] = 1
dp[1] = 1

for i in range(2, x):
    dp[i] = dp[i-1] + dp[i-2]

print(dp[4])
```

---

## Problemi Consigliati
(difficolta' molto indicative, sono tutti relativamente facili una volta che capite il meccanismo)
**EASY** - [`dogtrick`](https://training.olinfo.it/task/ois_dogtrick)
**MEDIUM** - [`treni`](https://training.olinfo.it/task/preoii_treni)
**HARD** - [`nonna`](https://training.olinfo.it/task/ois_nonna)
