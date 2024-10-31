# Competitive Programming (CP)
Lezione 5: Grafi

---

## Risorse
Tutto il materiale del corso puo' essere trovato su https://github.com/lorenzo-frittoli/cp-course
![[static/repo_qrcode.png|250]]

---

## Esempio: Grafo
```mermaid
graph TD;
N1(Nodo 1) --- N2(Nodo 2) ---N3(Nodo 3) --- N1
N1 --- N4(Nodo 4) --- N5(Nodo 5) --- N2
N3 --- N6(Nodo 6)
```

---

## Teoria: cos'e' un grafo
Un grafo rappresenta una "rete" di elementi connessi.

E' composto da **nodi** connessi da **archi** o **edges**.

---

## Esempio: Grafo Orientato
```mermaid
graph TD;
N1(Nodo 1) --> N2(Nodo 2) -->N3(Nodo 3) --> N1
N5(Nodo 5) --> N2
N5 --> N4(Nodo 4) --> N1
N3 --> N6(Nodo 6)
N3 --> N5
N1 --> N3
```

---

## Teoria: Grafi Orientati
Si dicono **diretti** o **orientati** quei grafi i cui **archi** hanno un **senso di percorrenza**.

In altre parole, gli archi non solo linee ma **frecce**.

---

## Esempio: Albero
```mermaid
graph TD;
N0("Nodo 0 (radice)") --- N1("Nodo 1 (foglia)")
N0 --- N2(Nodo 2) 
N0 --- N3(Nodo 3)
N2 --- N4("Nodo 4 (foglia)")
N2 --- N5("Nodo 5 (foglia)")
N3 --- N6("Nodo 6 (foglia)")
```

---

## Teoria: Alberi
Un albero e' un grafo **aciclico non orientato**.

Il "punto di partenza" e' detto **radice**.

Tutti i nodi tranne la radice hanno un **genitore** (il nodo sopra di loro) e possono avere dei **figli** (i nodi sotto di loro).

I nodi **senza figli** sono detti **foglie**.

Un albero e' detto **radicato** se hai deciso qual e' la radice.

---

## Teoria Implementativa
Possiamo implementare un grafo **orientato** salvando per ogni arco la **lista** dei **nodi** a cui si **collega**.

Se il grafo non e' orientato basta aggiungere due archi che vanno in direzioni opposte.

---

## Implementazione: Python

```py
N = int(input())
M = int(input())

graph = [[] for _ in range(N)]

for _ in range(M):
    start, end = map(int, input().strip().split())

    graph[start].append(end) # Aggiungi l'arco start -> end

    # Da fare se il grafo e' non orientato
    graph[end].append(start) # Aggiungi l'arco end -> start
```

---
