---
tipo: concetto
titolo: Anello e campo
tag: [algebra, matematica, strutture-algebriche]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Anello e campo

## Gerarchia delle strutture algebriche

$$\text{semigruppo} \subset \text{monoide} \subset \text{gruppo} \subset \text{anello} \subset \text{campo}$$

I concetti di semigruppo, monoide e gruppo sono trattati in [[Gruppo (struttura algebrica)]].

## Anello

Un **anello** $(A, +, \cdot)$ è un insieme $A$ con due operazioni che soddisfano:

1. $(A, +)$ è un gruppo **abeliano** (neutro $0$, inverso $-a$).
2. $(A, \cdot)$ è un **semigruppo** (chiusura + associatività).
3. **Distributività:** $a(b+c) = ab + ac$ e $(a+b)c = ac + bc$ per ogni $a,b,c$.

**Anello unitario:** $(A, \cdot)$ è un monoide (esiste $1 \in A$ con $1 \cdot a = a \cdot 1 = a$).

**Anello commutativo:** $a \cdot b = b \cdot a$ per ogni $a, b \in A$.

**Dominio d'integrità:** anello unitario commutativo senza **divisori dello zero** ($ab = 0 \Rightarrow a = 0$ o $b = 0$).

## Campo

Un **campo** $(F, +, \cdot)$ è un anello unitario commutativo in cui ogni elemento $\neq 0$ è invertibile rispetto alla moltiplicazione:

$$\forall a \in F \setminus \{0\}: \exists a^{-1} \in F \text{ con } a \cdot a^{-1} = 1$$

Equivalentemente: $(F \setminus \{0\}, \cdot)$ è un gruppo abeliano.

## Esempi

| Struttura | $+$ | $\cdot$ | Tipo |
|---|---|---|---|
| $(\mathbb{Z}, +, \cdot)$ | somma | prodotto | anello unitario commutativo (dominio d'integrità) |
| $(\mathbb{Q}, +, \cdot)$ | somma | prodotto | campo |
| $(\mathbb{R}, +, \cdot)$ | somma | prodotto | campo |
| $(\mathbb{C}, +, \cdot)$ | somma | prodotto | campo |
| $M_n(\mathbb{R})$ | somma matrici | prodotto matrici | anello unitario non commutativo ($n \geq 2$) |
| $\mathbb{Z}_n$ | somma mod $n$ | prodotto mod $n$ | anello unitario commutativo |
| $\mathbb{Z}_p$ ($p$ primo) | somma mod $p$ | prodotto mod $p$ | **campo** |

## $\mathbb{Z}_p$ è un campo per $p$ primo

**Proposizione.** $\mathbb{Z}_p$ è un campo $\Leftrightarrow$ $p$ è primo.

**Dimostrazione ($\Rightarrow$).** Se $p = ab$ con $1 < a, b < p$, allora $[a][b] = [0]$ ma $[a] \neq [0]$ e $[b] \neq [0]$: divisori dello zero, non campo.

**Dimostrazione ($\Leftarrow$).** Se $p$ primo e $\gcd(a, p) = 1$ per ogni $a \not\equiv 0$, allora per Bézout esiste $a^{-1} \pmod{p}$. Quindi ogni non-zero è invertibile. (cfr. [[Aritmetica modulare]])

## Polinomi su un campo

Su un campo $F$ si può costruire l'anello dei polinomi $F[x]$, che ha proprietà analoghe a $\mathbb{Z}$: algoritmo di divisione euclidea, MCD, irriducibili analoghi ai primi. In particolare $F[x]/(p(x))$ è un campo se $p(x)$ è irriducibile su $F$.

## Connessioni

- Strutture più semplici: [[Gruppo (struttura algebrica)]]
- Invertibilità in $\mathbb{Z}_n$: [[Aritmetica modulare]]
- Caratteristica di un campo: collegata a [[Principio di induzione]]
- Spazi vettoriali richiedono un campo scalare: [[Spazio vettoriale]]
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§2.2-2.3, §4, pp. 60-80, 110-117)
