---
tipo: concetto
titolo: Modello di Ising
tag: [mmf, fisica-statistica, probabilità]
cluster: fisica
fonti: 1
ultima-modifica: 2026-05-06
---

# Modello di Ising

Modello paradigmatico di **fisica statistica** per sistemi magnetici. $N$ spin $\sigma_i \in \{-1,+1\}$, con Hamiltoniana:

$$H(\sigma) = -h\sum_{i=1}^N \sigma_i - J\sum_{i=1}^{N-1} \sigma_i\sigma_{i+1}$$

dove $h$ = campo magnetico esterno, $J$ = costante di accoppiamento.

## Distribuzione di Boltzmann

$$p(\sigma) = \frac{e^{-\beta H(\sigma)}}{Z}, \qquad Z = \sum_\sigma e^{-\beta H(\sigma)}, \qquad \beta = \frac{1}{T}$$

## Metodo della matrice di trasferimento

Per calcolare $Z$ efficientemente si definisce:

$$T(\sigma,\sigma') = e^{-\beta h(\sigma,\sigma')}, \qquad h(\sigma_i,\sigma_{i+1}) = -\frac{h}{2}\sigma_i - J\sigma_i\sigma_{i+1} - \frac{h}{2}\sigma_{i+1}$$

Con condizioni periodiche: $Z = \text{Tr}(T^N)$. Con condizioni aperte: $Z = v^T T^{N-1} v$.

Complessità: $O(q^3 N)$ con $q = |\{-1,+1\}| = 2$.

## Autovalori e rappresentazione spettrale

$$T = \begin{pmatrix} e^{\beta(h+J)} & e^{-\beta J} \\ e^{-\beta J} & e^{\beta(-h+J)} \end{pmatrix}$$

Autovalori:

$$\lambda_\pm = e^{\beta J}\cosh(\beta h) \pm \sqrt{e^{2\beta J}\cosh^2(\beta h) - 2\sinh(2\beta J)}$$

**Rappresentazione spettrale:** $T^k = \lambda_+^k v_+v_+^T + \lambda_-^k v_-v_-^T$.

Per $N \to \infty$: $\lambda_+ \gg \lambda_-$, e:

$$F = -T\log Z \approx -TN\log\lambda_+, \qquad f = F/N = -T\log\lambda_+$$

## Magnetizzazione e correlazioni

**Magnetizzazione per spin** ($N\to\infty$):

$$m = -\frac{\partial f}{\partial h} = \frac{\sinh(\beta h)}{\sqrt{\sinh^2(\beta h) + e^{-4\beta J}}}$$

Casi limite: $J=0 \Rightarrow m = \tanh(\beta h)$; $J\to\infty \Rightarrow m = \text{sgn}(h)$.

**Correlazione tra spin** a distanza $r = j-i$ (per $N\to\infty$, $h=0$):

$$C_{ij} = \mathbb{E}[\sigma_i\sigma_j] - \mathbb{E}[\sigma_i]\mathbb{E}[\sigma_j] = \left(\frac{\lambda_-}{\lambda_+}\right)^r = e^{-r/\xi}$$

con **lunghezza di correlazione** $\xi = -1/\log\tanh(\beta J)$.

In 1D le correlazioni decadono esponenzialmente: **non c'è transizione di fase** a $T > 0$.

## Gas reticolare

Il modello di Ising con $J$ descrive anche un **gas reticolare**: $n_i = (1+\sigma_i)/2 \in \{0,1\}$, $\mu$ potenziale chimico. La distribuzione di Boltzmann diventa quella di un gas di Fermi-Dirac su reticolo.

## Connessioni

- Fondamento: [[Principio di massima entropia]], [[Catena di Markov]]
- Generalizzazione a campo medio: [[Modello di Curie-Weiss e Hopfield]]
- Strumento: [[Autovalori e autovettori]] (diagonalizzazione di $T$)
- Corsi: [[Modelli Matematici per la Fisica II]]

## Fonti

- [[Dispense MMFII — Galletti]] (§4, pp. 33-44)
