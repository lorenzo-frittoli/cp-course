# Competitive Programming (CP)
Lezione 1: Analisi di Complessita'

---

## Risorse
Tutto il materiale del corso puo' essere trovato su https://github.com/lorenzo-frittoli/cp-course
![[static/repo_qrcode.png|250]]

---

## La Complessita'
La complessita' (temporale) indica **l'aumento** del **tempo di esecuzione** di un programma al **crescere dell'input**.

Puo' anche essere vista come **l'ordine di grandezza** del **numero di operazioni** svolte dal programma.

La complessita' viene espressa come funzione del valore di input, e si dice $O(...)$ (vedi prossima slide).

---

## Esempio 0
Dato un numero $N$, restituisci $2N$.

---

## Esempio 1
Data una lista $V$ di $N$ interi, restituisci la somma dei suoi elementi.

---

## Esempio 2
Data una lista, restituisci la sommatoria di 

---

## Esempio di Complessita'
Dato un input di dimensione $N$, ecco alcuni esempi di possibili complessita' del programma:
- $O(1)$
- $O(N)$
- $O(N logN)$
- $O(N^2)$

Un programma con complessita' $O(1)$ si dice vada in **tempo costante** o **istantaneo**.

---

## $O(1)$
Vanno in $O(1)$ tutte quelle operazioni che *non dipendono* dalla dimensione dell'**input**.
- Operazioni*    ->  `+`, `-`, `*`, `/`
- Radice*    ->  `sqrt(x)`
- Aggiungere o rimuovere un valore **alla fine** di una lista ->  `l.append(x)`, `l.pop()`

---

## $O(N)$
Vanno in $O(N)$ tutte quelle operazioni che richiedono di **iterare sull'input**.
- Cicli (dove N e' la loro durata) ->  `for`, `while`, list comprehension

----

## $O(NlogN)$
Sortare una lista di lunghezza $N$ va in $O(NlogN)$.

---

## Pessimismo Cosmico
Quando calcoliamo la complessita' consideriamo sempre **il caso peggiore**.

```py
sort([1,2,3])   # Caso migliore -> quasi istantaneo
sort([3,2,1])   # Caso peggiore -> N log N
# Consideriamo N log N come complessita'
```

---

## Unione di Complessita'
Il mio programma deve **sortare** una lista e poi **iterarla**.

Sortare la lista va in $O(NlogN)$, iterarla in $O(N)$, quindi la complessita' finale dovrebbe essere $O(NlogN + N)$, giusto...?

**NO**: per $N$ molto grandi, $NlogN >> N$, quindi $O(NlogN + N) = O(NlogN)$.

---

Queste slides non sono state usate perche' spiegare la complessita' veniva meglio senza slide, quindi sono incomplete.
