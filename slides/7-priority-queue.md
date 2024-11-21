# Competitive Programming (CP)
Lezione 7: Priority Queue

---

## Risorse
Tutto il materiale del corso puo' essere trovato su https://github.com/lorenzo-frittoli/cp-course
![[static/repo_qrcode.png|250]]

---

## Ripasso
Cosa sono queue e stack?
Suggerimento: [[./3-queue.md|Queue]]
Suggerimento: [[./4-stack.md|Stack]]

---

## Priority Queue
Una **priority queue** e' una **queue** che, al posto che **ordinare** per **ordine di arrivo**, ordina rispetto a dei **pesi**.
```
      push (A, 4)     push (C, 2)       get()

                (A, 4)          (C, 2)          (A, 4)
(A, 4)    =>              =>    (A, 4)    =>    
                (B, 7)          (B, 7)          (B, 7)

```

---

## Implementazione Artigianale
Possiamo pushare gli elementi a caso su una lista e prendere il massimo ogni volta.

Possimo pushare creare una lista ordinata inserendo gli elementi in mezzo alla lista.

---

## Complessita'
| **Struttura Dati** | **Push**    | **Get** | **Pop**     |
| ------------------ | ----------- | ------- | ----------- |
| Lista non Ordinata | $O(1)$      | $O(N)$  | $O(N)$      |
| Lista Ordinata     | $O(N)$      | $O(1)$  | $O(1)$      |
| Priority Queue     | $O(\log N)$ | $O(1)$  | $O(\log N)$ |

---

## Implementazione
```py

import queue

# Create a priority queue
pq = queue.PriorityQueue()

# Add elements to the queue with their respective priorities
pq.put((2, "Task 2"))
pq.put((1, "Task 1"))
pq.put((3, "Task 3"))

# Remove elements from the queue based on their priority
while not pq.empty():
    priority, task = pq.get()
    print(f"Priority: {priority}, Task: {task}")

```

---
