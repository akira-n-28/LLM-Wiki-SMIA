---
tipo: concetto
titolo: Modello di Curie-Weiss e Hopfield
tag: [mmf, fisica-statistica, machine-learning, reti-neurali]
cluster: fisica
fonti: 1
ultima-modifica: 2026-05-06
---

# Modello di Curie-Weiss e Modello di Hopfield

## Modello di Curie-Weiss (Ising fully connected)

Variante del modello di Ising in cui **ogni spin interagisce con tutti gli altri** (grafo completo). Hamiltoniana:

$$H(\sigma) = -\frac{J}{2N}\sum_{i,j=1}^N \sigma_i\sigma_j - h\sum_{i=1}^N\sigma_i = -\frac{J}{2N}M^2(\sigma) - hM(\sigma)$$

con $M(\sigma) = \sum_i \sigma_i$ magnetizzazione totale.

### Energia libera e campo medio

Per $N\to\infty$, la somma su $M$ è dominata dal minimo dell'energia libera:

$$f(m) = -\frac{J}{2}m^2 - hm - TS(m), \qquad S(m) = -\frac{1+m}{2}\log\frac{1+m}{2} - \frac{1-m}{2}\log\frac{1-m}{2}$$

La magnetizzazione per spin $m = M/N$ soddisfa l'**equazione di campo medio**:

$$\boxed{m = \tanh\!\left(\beta(Jm + h)\right)}$$

### Transizione di fase

Per $h = 0$:
- Se $T > T_c = J$ ($\beta J < 1$): unica soluzione $m=0$ (**fase paramagnetica**).
- Se $T < T_c = J$ ($\beta J > 1$): tre soluzioni; le due soluzioni $m = \pm\bar{m} \neq 0$ sono stabili (**fase ferromagnetica**).

La temperatura critica è $T_c = J$. Per $T \to T_c^-$ la magnetizzazione appare per **biforcazione** da $m=0$.

### Suscettività magnetica

$$\chi = \frac{dm}{dh} = \frac{\beta(1-m^2)}{1 - \beta J(1-m^2)}$$

Diverge per $T \to T_c^+$ (con $h=0$, $m=0$): $\chi \sim 1/(T - T_c)$.

### Teoria di campo medio generalizzata

Su un reticolo $d$-dimensionale con $2d$ vicini, il campo medio prevede:

$$m = \tanh(\beta(h + J \cdot 2d \cdot m))$$

L'approssimazione migliora al crescere della dimensione $d$ (per il TLC). In dimensione infinita (grafo completo) è **esatta**.

| $d$ | $T_c^{\text{simulazione}}/J$ |
|---|---|
| 2 | 0.567 |
| 3 | 0.752 |
| 4 | 0.835 |
| $\infty$ | 1 (campo medio) |

## Modello di Hopfield (memoria associativa)

Rete neurale a spin in cui ogni neurone $\sigma_i \in \{-1,+1\}$ è connesso a tutti gli altri tramite **sinapsi** $J_{ij}$.

### Regola di Hebb (singola memoria $\xi \in \{-1,+1\}^N$)

$$J_{ij} = \frac{\xi_i\xi_j}{N}, \qquad \varphi_i(t) = \sum_j J_{ij}\sigma_j(t)$$

Aggiornamento: $\sigma_i(t+1) = \text{sgn}(\varphi_i(t))$ (limite $\beta\to\infty$).

**Proprietà:** $\vec{\xi}$ è un punto fisso. Con stato iniziale $\vec{\sigma}(0) = \vec{\xi}$, il sistema rimane su $\vec{\xi}$.

**Magnetizzazione condensata:** $m(t) = \frac{\vec{\xi}\cdot\vec{\sigma}(t)}{N} \to m(t+1) = \tanh(\beta m(t))$.

### Memoria associativa (più memorie)

Per $P$ memorie $\{\xi^{(1)},\ldots,\xi^{(P)}\}$:

$$J_{ij} = \frac{1}{N}\sum_{k=1}^P \xi_i^{(k)}\xi_j^{(k)}$$

Il sistema converge alla memoria più vicina allo stato iniziale se $P \ll N$ (capacità $\sim 0.14N$ per pattern scorrelati).

### Connessione con Curie-Weiss

L'Hamiltoniana di Hopfield con una sola memoria è $H = -\frac{J}{2N}\sum_{ij}\xi_i\xi_j\sigma_i\sigma_j = $ Curie-Weiss con spin $\xi_i\sigma_i$.

## Connessioni

- Modello 1D: [[Modello di Ising]]
- Base teorica: [[Principio di massima entropia]], [[Entropia di Shannon]]
- Reti neurali: [[Multi-Layer Perceptron]], [[Recurrent Neural Network]]
- Grandi deviazioni: [[Teoria delle grandi deviazioni]]
- Corsi: [[Modelli Matematici per la Fisica II]]

## Fonti

- [[Dispense MMFII — Galletti]] (§5, pp. 45-59)
