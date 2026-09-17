---
tipo: concetto
titolo: Teorema di approssimazione universale
tag: [reti-neurali, teoria, ml]
cluster: ml
ultima-modifica: 2026-04-30
---

# Teorema di approssimazione universale

> **Teorema.** Sia $\Omega \subset \mathbb{R}^p$ compatto e $\sigma$ funzione logistica (o, più in generale, una qualunque funzione di attivazione non polinomiale). Lo spazio delle funzioni $\phi(x) = \sigma(W x + b)$ è **denso** in $C(\Omega)$. Cioè per ogni $f \in C(\Omega)$ continua e per ogni $\varepsilon > 0$ esistono $q \in \mathbb{N}$ e pesi $u_k, W_k, b_k$ tali che
> $$
> \left| f(x) - \sum_{k=1}^q u_k\, \phi_k(x) \right| \leq \varepsilon \quad \forall x \in \Omega.
> $$

In parole: una rete neurale con **un solo strato nascosto** sufficientemente largo può approssimare qualunque funzione continua su un compatto, con la precisione che si vuole.

## Cosa garantisce — e cosa no

✅ **Garantisce:**
- Esistenza di pesi che realizzano l'approssimazione.
- L'MLP è una classe di modelli "abbastanza ricca" da non essere intrinsecamente limitata.

❌ **Non garantisce:**
- Quanti neuroni $q$ servono (in pratica può essere enorme).
- Che esista un algoritmo che *trova* quei pesi in tempo ragionevole.
- Generalizzazione: dice solo che si può fittare una funzione, non che la rete generalizzerà bene su nuovi dati.
- Profondità necessaria: nel teorema basta un layer; in pratica le reti **profonde** approssimano molto più efficientemente certe famiglie di funzioni (esponenzialmente meno parametri rispetto alle shallow).

## Parente concettuale

È analogo, in spirito, a [[Regressione polinomiale|Stone-Weierstrass]] (i polinomi sono densi in $C[a,b]$): garanzia di approssimabilità, non di addestrabilità.

## Collegamenti

- Riguarda: [[Multi-Layer Perceptron]]
- Confronta con: [[Regressione polinomiale]] (Stone-Weierstrass)
- Discusso in: [[Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (Teorema 5.1, p. 17)
