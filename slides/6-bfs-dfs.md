# Competitive Programming (CP)
Lezione 6: BFS e DFS

---

## Risorse
Tutto il materiale del corso puo' essere trovato su https://github.com/lorenzo-frittoli/cp-course
![[static/repo_qrcode.png|250]]

---

## Problema
Dato un ALBERO e un nodo $A$, trova il nodo $B$ piu' distante da esso.

---
## Problema
Dato un grafo e un nodo $A$, trova il nodo $B$ piu' lontano.

---

## Problema
Dato un albero radicato, trova tutti i nodi che hanno una foglia a distanza $X$ nel proprio sottoalbero.

---

## Problema
Dato un albero radicato, trova tutti i nodi il cui sottoalbero ha una somma degli indici dei nodi pari.

---

## BFS
Breadth First Search (per alberi e grafi)\
Visito i nodi a 'livelli'.

---

- Visito la radice: $0^o$ livello.
	- Quando sto visitando la radice, aggiungo alla queue i suoi figli che si troveranno nel $1^o$ livello
	
- Rimarranno nella queue i nodi del $1^o$ livello.
	- Quando sto visitando un nodo del $1^o$ livello, aggiungo alla queue i suoi figli che si troveranno nel $2^o$ livello
	
- Rimarranno nella queue i nodi del $2^o$ livello.
	- Quando sto visitando un nodo del $2^o$ livello, aggiungo alla queue i suoi figli che si troveranno nel $3^o$ livello

---
## DFS ricorsiva

Depth First Search (solo per alberi)\
Parto dalla radice dell'albero.

#### Visita di un nodo:
- Visito tutti i nodi nel sottoalbero del $1^o$ figlio
- Visito tutti i nodi nel sottoalbero del $2^o$ figlio
- Visito tutti i nodi nel sottoalbero del $3^o$ figlio
- ...
- Ho visitato tutti i nodi nel mio sottoalbero.

---

## Implementazione:
#### DFS ricorsiva

```py
def dfs(current, parent):
	'''L'albero è salvato nella variabile `tree` come grafo
	   (liste di adiacenza)'''
	results = []
	for neighbour in tree[current]:
		# Evitiamo di "risalire" l'albero visitando il padre
		if neighbour == parent:
			continue
		# Visito il figlio, del quale sono il padre
		results.append(
			dfs(neighbour, current)
		)
	return doSomething(results) # A seconda del problema
```

```py
# Chiamo `dfs` sulla radice.
# La radice non ha padre: se passo `-1` nessun nodo verrà
# identificato come il padre all'interno dell'if

result = dfs(radice, -1)
```

---

## Implementazione:
#### DFS iterativa

```py
'''L'albero è salvato nella variabile `tree` come grafo
   (liste di adiacenza)'''
stack = [radice]
visited = [False for _ in range(len(tree))]
while len(stack):
	current = stack[-1]
	stack.pop()
	visited[current] = True
	doSomething(current) # A seconda del problema
	for neighbour in tree[current]:
		# Evitiamo di "risalire" l'albero visitando il padre
		if visited[neighbour]:
			continue
		stack.append(neighbour)
```

```py
'''L'albero è salvato nella variabile `tree` come grafo
   (liste di adiacenza)'''
stack = [radice]
while len(stack):
	current = stack[-1]
	stack.pop()
	visited[current] = True
	doSomething(current) # A seconda del problema
	for child in tree[current]:
		stack.append(child)
```

---

## Implementazione: 