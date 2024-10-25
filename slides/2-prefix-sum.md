# Competitive Programming (CP)
Lezione 2: Somme Prefisse (prefix sum)

---

## Risorse
Tutto il materiale del corso puo' essere trovato su https://github.com/lorenzo-frittoli/cp-course
![[static/repo_qrcode.png|250]]

---

## Problema
Data una lista $V$ di $N$ interi e due liste $S$, $E$ di lunghezza $M$ che denotano i punti di inizio e di fine di altrettanti intervalli (incluso-escluso), calcola la somma dei valori di $V$ all'interno di ogni intervallo.

---

## Naive: Teoria
Per ogni intervallo di $s \in S, e \in E$, restituisco la somma dei valori di $V$ in quell'intervallo.
$$\forall s \in S, \forall e \in E \space \Rightarrow output = \sum_{i=s}^{e} V_i$$

La complessita' temporale e' $O(N M)$.

---

## Naive: Implementazione
```py
def naive(N, M, V, S, E):
    output = []
    for i in range(M):
        output.append(0)
        for j in range(E[i]-S[i]):
            output[-1] += V[S[i] + j]

    return output
```

---

## Naive: Implementazione (ma scritta meglio)
```py
def naive(N, M, V, S, E):
    output = []
    # for x in X
    # -> itera su X, chiamando l'elemento attuale x
    # zip(X, Y)
    # -> [[X[0], Y[0]], [X[1], Y[1]], [X[2], Y[2]], ...]
    for s, e in zip(S, E):
        output.append(0)
        # range(s=0, e, step=1)
        for i in range(s, e):
            output[-1] += V[i]

    return output
```

---

## Prefixsum: Teoria
Creo un vettore $ps$ che per ogni indice $i$ contiene la somma degli elementi di $V$ da $0$ a $i$.
$$se\ i = 0,\ ps_i = 0$$
$$altrimenti,\ ps_i = \sum_{j=0}^{i-1} V_i$$

Siccome $ps_{i+1} = ps_i + V_{i+1}$, posso computare ogni valore di $ps$ in $O(1)$.

$ps$ ha lunghezza $N$, quindi computare $ps$ va in $O(N)$.

Per calcolare la somma sull'intervallo $s, e$ basta fare $ps_e - ps_s$, in $O(1)$.

La complessita' finale e' quindi $O(N + M)$.

---

## Prefixsum: Implementazione
```py
def prefixsum(N, M, V, S, E):
    ps = [0]
    for v in V:
        ps.append(ps[-1]+v)

    output = []
    for s,e in zip(S, E):
        output.append(ps[e] - ps[s])

    return output
```

---

## Prefixsum: Implementazione (ma piu' carina)
```py
def prefixsum(N, M, V, S, E):
    ps = [0]
    # List Comprehension
    # -> L2 = [2*l for l in L1]
    # L1 = [0, 3, 2]
    # -> L2 = [0, 6, 4]
    ps = [ps[-1] + v for v in [0]+V]

    return [ps[e] - ps[s] for e,s in zip(E,S)]
```
