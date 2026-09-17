---
tipo: concetto
titolo: Algoritmo di Euclide
tag: [algebra, matematica, aritmetica, algoritmi]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Algoritmo di Euclide

Metodo per calcolare il [[Massimo comun divisore]] di due interi basato sul fatto che:

$$\text{MCD}(a, b) = \text{MCD}(b, r) \quad \text{dove } a = bq + r, \; 0 \leq r < b$$

## Algoritmo (versione base)

Dati $a > b > 0$, si eseguono divisioni euclidee successive:

$$\begin{aligned}
a &= b\,q_1 + r_1 & 0 \leq r_1 < b \\
b &= r_1\,q_2 + r_2 & 0 \leq r_2 < r_1 \\
&\vdots \\
r_{n-2} &= r_{n-1}\,q_n + r_n & 0 \leq r_n < r_{n-1} \\
r_{n-1} &= r_n\,q_{n+1} + 0
\end{aligned}$$

**Termina** perché i resti formano una successione strettamente decrescente di interi non negativi. L'ultimo resto non nullo $r_n = \text{MCD}(a,b)$.

**Esempio:** $a = 108, b = 45$:
$$108 = 2 \cdot 45 + 18, \quad 45 = 2 \cdot 18 + 9, \quad 18 = 2 \cdot 9 + 0 \quad \Rightarrow \text{MCD} = 9$$

## Algoritmo esteso (Bézout)

Risalendo le equazioni si esprime il MCD come combinazione lineare $d = sa + tb$.

**Esempio:** $9 = 45 - 2 \cdot 18 = 45 - 2(108 - 2 \cdot 45) = -2 \cdot 108 + 5 \cdot 45$, quindi $s = -2, t = 5$.

## Calcolo dell'inverso in $\mathbb{Z}_n$

Per trovare $a^{-1}$ in $\mathbb{Z}_n$:
1. Verificare $\text{MCD}(a, n) = 1$ (se $\neq 1$ non esiste l'inverso).
2. Scrivere l'identità di Bézout $1 = sa + tn$: allora $s \equiv a^{-1} \pmod{n}$.

**Esempio:** inverso di $31$ in $\mathbb{Z}_{290}$: l'algoritmo esteso dà $131 \cdot 31 - 10 \cdot 290 = 1$, quindi $31^{-1} \equiv 131 \pmod{290}$.

## Connessioni

- Calcola: [[Massimo comun divisore]]
- Usato per: [[Aritmetica modulare]] (inversi moltiplicativi), equazioni diofantine
- Versione numerica (sistemi lineari): [[Sistemi lineari — metodi diretti]]
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§1.7.1, pp. 47-57)
