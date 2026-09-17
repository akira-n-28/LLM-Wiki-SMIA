---
tipo: concetto
titolo: Principio di induzione
tag: [algebra, matematica, logica]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Principio di induzione

Il principio di induzione è il quinto postulato di Peano per $\mathbb{N}$. Ne esistono tre forme equivalenti:

## Tre forme equivalenti

**N₃ — Induzione semplice (Peano):**
$$[P(0) \land \forall k \geq 0 (P(k) \Rightarrow P(k+1))] \Rightarrow \forall n: P(n)$$

**I — Induzione forte:**
$$P(0) \land [\forall 0 \leq k < n, P(k) \Rightarrow P(n)] \Rightarrow \forall n: P(n)$$

Il passo induttivo usa l'ipotesi $P(0) \land P(1) \land \ldots \land P(n-1)$ per dimostrare $P(n)$.

**M — Principio del buon ordinamento:**
$$\forall S \subseteq \mathbb{N}, S \neq \emptyset \Rightarrow \exists m \in S: m \leq t \;\forall t \in S$$

**Teorema:** le tre forme N₃, I, M sono equivalenti tra loro.

## Schema di applicazione

Per dimostrare $\forall n \geq n_0: P(n)$:
1. **Caso base:** verificare $P(n_0)$.
2. **Ipotesi induttiva:** assumere $P(k)$ vera per un certo $k \geq n_0$.
3. **Passo induttivo:** dimostrare $P(k+1)$ usando l'ipotesi.

## Esempi canonici

- $\sum_{k=1}^n k = \frac{n(n+1)}{2}$
- $\sum_{k=1}^n (2k-1) = n^2$
- Fibonacci: $F_1^2 + F_2^2 + \ldots + F_n^2 = F_n \cdot F_{n+1}$
- Ogni naturale $\geq 2$ si fattorizza in irriducibili (parte dell'unicità di fattorizzazione)

## Assiomi di Peano

Gli assiomi fondamentali (P1–P5) definiscono $\mathbb{N}$ come il più piccolo insieme che contiene lo zero e il successore di ogni suo elemento:
- P1: $0 \in \mathbb{N}$
- P2: $n \in \mathbb{N} \Rightarrow \sigma(n) \in \mathbb{N}$
- P3: $\sigma$ è iniettiva
- P4: $0$ non è successore di nessuno
- P5: (induzione) se $U \ni 0$ e $n \in U \Rightarrow \sigma(n) \in U$, allora $U = \mathbb{N}$

## Connessioni

- Equivalente a: [[Relazione d'ordine]] (principio del buon ordinamento)
- Usato per: [[Massimo comun divisore]] (esistenza del MCD), [[Algoritmo di Euclide]] (terminazione), [[Teorema di Lagrange]]
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§1.4, pp. 33-39)
