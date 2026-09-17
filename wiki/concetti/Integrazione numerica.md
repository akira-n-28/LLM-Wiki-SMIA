---
tipo: concetto
titolo: Integrazione numerica
tag: [calcolo-numerico, analisi, metodi-numerici]
cluster: numerico
fonti: 1
ultima-modifica: 2026-05-05
---

# Integrazione numerica (Quadratura)

Le formule di **quadratura numerica** approssimano l'integrale definito $\int_a^b f(x)\,dx$ tramite una combinazione lineare dei valori di $f$ in $n+1$ nodi:

$$I_n(f) = \sum_{i=0}^{n} w_i\, f(x_i)$$

con pesi $w_i$ e nodi $x_i$ opportunamente scelti.

## Formule di Newton-Cotes

Basate sull'integrazione del polinomio interpolante di $f$ sui nodi **equidistanti** $x_i = a + ih$, $h=(b-a)/n$.

### Rettangoli (punto medio, $n=1$)

$$\int_a^b f(x)\,dx \approx (b-a)\,f\!\left(\frac{a+b}{2}\right)$$

Errore composito su $m$ sottointervalli di ampiezza $h$: $O(h^2)$.

### Trapezi ($n=1$ per ogni sottointervallo)

$$\int_a^b f(x)\,dx \approx \frac{h}{2}\left[f(x_0) + 2f(x_1) + \ldots + 2f(x_{n-1}) + f(x_n)\right]$$

**Errore composito:** $-\frac{h^2(b-a)}{12}\,f''(\xi)$ per qualche $\xi\in(a,b)$ — ordine $O(h^2)$.

**Nota:** la formula dei trapezi è esatta per polinomi di grado $\leq 1$.

### Cavalieri-Simpson ($n=2$ per ogni coppia)

Richiede $n$ pari; su ogni coppia di sottointervalli usa un polinomio di grado 2:

$$\int_a^b f\,dx \approx \frac{h}{3}\left[f(x_0) + 4f(x_1) + 2f(x_2) + 4f(x_3) + \ldots + 4f(x_{n-1}) + f(x_n)\right]$$

**Errore composito:** $-\frac{h^4(b-a)}{180}\,f^{(4)}(\xi)$ — ordine $O(h^4)$.

Curiosamente, Simpson è esatto per polinomi di grado $\leq 3$ (grado di esattezza 3, non 2): la simmetria della formula annulla il termine di errore di ordine 3.

## Quadratura di Gauss

Invece di nodi equidistanti, si scelgono $n+1$ nodi e $n+1$ pesi **ottimali** (radici dei polinomi di Legendre su $[-1,1]$):

$$\int_{-1}^{1} f(x)\,dx \approx \sum_{i=0}^{n} w_i\, f(x_i)$$

**Grado di esattezza:** $2n+1$ — integra esattamente polinomi fino al grado $2n+1$ usando solo $n+1$ valutazioni di $f$. Con la stessa quantità di nodi, Gauss è molto più preciso di Newton-Cotes.

**Svantaggi:** i nodi Gauss non includono i bordi $\{a,b\}$ (problema per $f$ discontinua sul bordo) e non sono equidistanti (servono dati a punti non uniformi).

## Confronto

| Formula           | Nodi necessari | Ordine errore | Grado esattezza |
|-------------------|----------------|---------------|-----------------|
| Rettangoli        | $m+1$          | $O(h^2)$      | 1               |
| Trapezi           | $m+1$          | $O(h^2)$      | 1               |
| Cavalieri-Simpson | $m+1$ ($m$ pari) | $O(h^4)$  | 3               |
| Gauss ($n+1$ pt.) | $n+1$          | esatta p.$\leq 2n+1$ | $2n+1$ |

## Legame con l'interpolazione

Le formule di Newton-Cotes derivano dall'integrazione esatta del polinomio interpolante di $f$ sullo stesso insieme di nodi: cfr. [[Interpolazione di Lagrange]].

## Connessioni

- Prerequisito di: [[Metodi numerici per ODE]] (analogia tra discretizzazione e quadratura)
- Richiede: [[Interpolazione di Lagrange]]
- Discusso in: [[Metodi Numerici]]

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
