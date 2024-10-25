# Competitive Programming (CP)

Lezione 0: Introduzione

---

## Risorse
Tutto il materiale del corso puo' essere trovato su https://github.com/lorenzo-frittoli/cp-course
![[static/repo_qrcode.png|250]]

---

## Chi Siamo
Immagine bellissima, grazie Mosi
![[static/noi.jpeg|300]]

---

## Problema 1
Marco e' l'unico insegnante che non ha ancora compiuto 18 anni. 
Aiuta Marco a creare un programma che, dato il suo anno di nascita `nato` e l'anno corrente `corrente`, restituisce fra quanti anni sara' il suo 18esimo compleanno.

---

### Teoria 1

$$compleanno = nato + 18$$

Vogliamo sapere fra quanti anni Marco compiera' 18 anni, quindi la differenza fra `compleanno` e `corrente`.

$$x = compleanno - corrente$$

$$x = (nato + 18) - corrente$$

$$\bf{x = nato - corrente + 18}$$

---

### Pseudocodice 1

```
ricevo nato, corrente    # input

x = nato - corrente + 18    # elaborazione

restituisco x    # output
```

---
### Implementazione 1

```py
nato = int(input())
corrente = int(input())

x = nato - corrente + 18

print(x)
```

---

## Problema 2
Luca ha un gran quantitativo di Giandomenici d'Oro, ma vuole verificarne di non averne perso nessuno.

Fortunatamente ha tenuto conto, per ognuna delle `N` premiazioni, quanti Giandomenici gli sono stati assegnati; sa anche il numero di Giandomenici `X` che ha in questo momento nella sua collezione.

Scrivi un programma che legga questi dati e restituisca `vero` se Luca ha perso qualche Giandomenico, altrimenti `falso`.

---

### Teoria 2
Per sapere se Luca ha perso qualche Giandomenico d'Oro, possiamo calcolare il numero totale di Giandomenici che ha ricevuto e compararlo con quanti ne possiede.

Per calcolare il totale possiamo ciclare sulle premiazioni e aggiungere il numero di Giandomenici a un totale. Questo pattern si chiama *accumulatore*.

Ci basta poi comparare il totale al numero posseduto: se sono uguali restituiamo `falso`, altrimenti `vero`.

---

### Pseudocodice 2
```
input X, N

totale = 0

ripeti N volte:
    totale = totale + input

se totale == X:
    restituisci falso
altrimenti:
    restituisci vero
```

---

### Implementazione 2

```py
X = int(input())
N = int(input())

tot = 0
for i in range(N):
    tot += int(input())

if tot == X:
    print(False)
else:
    print(True);
```

---

## Problema 3

<span style="font-size: 80%">
Mosi deve creare la squadra femminile di Matematica. Per fare questo, fa una gara interna fra le `N` ragazze in cui l'i-esima ragazza ottiene un punteggio `P_i`.

Tutte queste ragazze (ovviamente) appartengono al lungo stuolo di ammiratrici di Mosele e lui ha un'amicizia $A_i$ con l'i-esima ragazza.

Siccome le gare di Matematica sono una mafia, lo score finale della i-esima ragazza e' $P_i + A_i$.

La squadra deve essere formata dalle $M$ ragazze con lo score piu' alto.

Restituisci gli score della squadra finale.
</span>

---

### Teoria 3

Per salvarci una lista di valori, dobbiamo utilizzare... le **liste** (o *vector*, se usate C++).

Per ogni $i$ da $0$ a $N$ ci salviamo $P_i$ e $A_i$ nelle liste $P$ e $A$.

Sommiamo fra di loro le due liste per ottenere la lista di score finali $S$.

Ordiniamo questa lista in ordine decrescente e restituiamo i primi $M$ valori.

---

### Pseudocodice 3

```
input N, M
input P, A

per i da 0 a N:
    aggiungi P[i]+A[i] ad S

ordina S

per i da 0 a M:
    restituisci S[i]
```

---

### Implementazione 3

```py
N = int(input())
M = int(input())

P = []
A = []

for i in range(N):
    P[i] = int(input())

for i in range(N):
    A[i] = int(input())

S = []

for i in range(N):
    S[i].append(A[i] + P[i])

sort(S[i])

print(S[:M])
```
