# Competitive Programming (CP)
Lezione 4: Stack

---

## Risorse
Tutto il materiale del corso puo' essere trovato su https://github.com/lorenzo-frittoli/cp-course
![[static/repo_qrcode.png|250]]

---

## Teoria: cos'e' una stack
Una stack e' una **pila**, come quella delle carte a rubamazzetto. 

Piu' formalmente: una struttura dati in cui possiamo **inserire** elementi e **rimuoverli** nell'**ordine inverso** in cui li abbiamo **inseriti**.

Per questo e' detta *First In Last Out*, o **FILO**.

---

## Teoria: le operazioni di una stack

| **Nome**  | **Funzionalita'**                 | **Complessita'** |
| --------- | --------------------------------- | ---------------- |
| push      | Aggiungi un elemento              | $O(1)$           |
| top       | Restituisci il primo elemento     | $O(1)$           |
| pop       | Rimuovi il primo elemento         | $O(1)$           |
| size      | Restituisci il numero di elementi | $O(1)$           |
| empty     | La stack e' vuota? Vero o falso   | $O(1)$           |

A volte `top` e `pop` sono uniti in un solo metodo.

---

## Implementazione: Python
Possiamo usare una lista per implementare la stack.

```py
s = []  # Inizializzo la stack

s.append("A")   # pusha la stringa "A"
s.append("B")   # pusha la stringa "B"

print(len(s))    # lunghezza stack -> 2

print(q[-1])    # elemento in cima -> "B"
q.pop()         # rimuovo "B"

print(q[-1])    # elemento in cima -> "A"
q.pop()         # rimuovo "A"

print(len(q))   # lunghezza stack -> 0
```

---
