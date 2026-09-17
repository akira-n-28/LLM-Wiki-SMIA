---
tipo: concetto
titolo: Algoritmo del percettrone
tag: [ottimizzazione, reti-neurali, machine-learning]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Algoritmo del percettrone

Primo algoritmo di apprendimento automatico (1943, McCulloch-Pitts; formalizzato da Rosenblatt 1958). Classifica punti linearmente separabili aggiornando i pesi quando commette un errore.

## Modello

**Neurone artificiale**: ingresso $x \in \mathbb{R}^n$, pesi $w \in \mathbb{R}^n$, soglia $\theta$, funzione di attivazione a gradino:
$$
y(x, w, \theta) = g(w^T x - \theta), \quad g(t) = \begin{cases} 1 & t \geq 0 \\ -1 & t < 0 \end{cases}
$$

Il bias $\theta$ può essere incorporato aggiungendo $x_0 = 1$ e peso $w_0 = -\theta$.

## Training set e problema

$TS = \{(x^p, y^p): x^p \in \mathbb{R}^n, y^p \in \{-1,+1\}, p=1,\ldots,P\}$.

$A = \{x^p: y^p = 1\}$, $B = \{x^p: y^p = -1\}$.

Obiettivo: trovare $w$ tale che $y^p (w^T x^p) > 0 \;\forall p$ (classificazione corretta di tutti i campioni).

## Algoritmo

```
Inizializza w(0) arbitrariamente
for k = 0, 1, 2, ...:
    scegli xp ∈ A ∪ B
    if yp(w(k)^T xp) > 0:
        w(k+1) = w(k)           # classificato correttamente
    else:
        w(k+1) = w(k) + yp xp  # aggiornamento
```

**Regola di aggiornamento**: $w(k+1) = w(k) + y^p x^p$. Dopo l'aggiornamento il termine migliora:
$$
y^p w(k+1)^T x^p = y^p w(k)^T x^p + (y^p)^2 \|x^p\|^2 > y^p w(k)^T x^p
$$

## Convergenza

**Teorema (Rosenblatt)**: se $A$ e $B$ sono **linearmente separabili** ($\exists w^*: y^p (w^*)^T x^p > 0 \;\forall p$), allora l'algoritmo del percettrone determina in un numero finito di iterazioni un vettore $w^*$ di classificazione corretta.

**Limite**: l'ipotesi di separabilità lineare è molto forte. Inoltre, il percettrone non trova l'iperpiano ottimale (quello a massimo margine).

## Estensione con funzione di attivazione differenziabile

Sostituendo $g(t) = \text{sgn}(t)$ con $g(t) = \tanh(t) = (e^t - e^{-t})/(e^t + e^{-t})$ (che è $C^\infty$):
$$
\min_w E(w) = \frac12 \sum_{p=1}^P \bigl(y^p - g(w^T x^p)\bigr)^2
$$

Problema non lineare e non convesso, risolto con [[Discesa del gradiente]] o [[Gradiente coniugato]].

Con la funzione identità $g(t) = t$: il problema diventa minimi quadrati lineari $\min_w \frac12 \|Xw - Y\|^2$.

## Connessione con [[Stochastic Gradient Descent]]

L'algoritmo del percettrone è un metodo incrementale con passo unitario e funzione di attivazione a gradino. La versione continua con $\tanh$ corrisponde a SGD su $E(w) = \sum_p E_p(w)$:
$$
w_{k+1} = w_k - \eta \nabla E_{p(k)}(w_k)
$$

## Collegamento con i corsi

- [[Ottimizzazione]]: §5, metodi incrementali.
- [[Machine Learning]]: precursore del [[Multi-Layer Perceptron]] e della [[Backpropagation]].
- [[Fondamenti di Intelligenza Artificiale]]: problema XOR mostra i limiti del percettrone a singolo strato.

## Fonti

- [[Dispense Ottimizzazione — Galletti]] (§5, pp. 38-42)
