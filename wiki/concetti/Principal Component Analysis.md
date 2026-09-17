---
tipo: concetto
titolo: Principal Component Analysis
tag: [ml, algebra-lineare, dimensionality-reduction]
cluster: ml
ultima-modifica: 2026-04-30
---

# Principal Component Analysis (PCA)

Tecnica di riduzione di dimensionalità lineare. Data una matrice di dati centrata $X \in \mathbb{R}^{d \times n}$ (colonne = campioni, media di riga zero), si cercano $k \leq d$ direzioni ortonormali $w_1, \ldots, w_k$ che:

a) **massimizzano** la varianza dei dati proiettati;
b) **minimizzano** l'errore di ricostruzione.

Le due formulazioni sono equivalenti.

## Derivazione (varianza massima)

Per una direzione unitaria $w$ la varianza della proiezione è $w^\top C w$ con $C = X X^\top$ matrice di covarianza. Si risolve

$$
\max_{\|w\|_2 = 1} w^\top C w
$$

usando il [[Quoziente di Rayleigh]]: il massimo è l'**autovalore dominante** $\lambda_1$ e si raggiunge sull'autovettore associato $u_1$ (prima componente principale). Le componenti successive si ottengono imponendo ortogonalità con le precedenti.

## Algoritmo

1. **Centra** i dati: $X \leftarrow X - \mathbf{1}\mu^\top$.
2. **Covarianza**: $C = \frac{1}{n} X X^\top$.
3. **Eigendecomposizione**: $C = U \mathrm{diag}(\lambda_1, \ldots, \lambda_d) U^\top$.
4. **Seleziona** i primi $k$ autovettori (ordine decrescente di $\lambda$). Spesso $k$ è scelto in modo che $\sum_{i=1}^k \lambda_i / \sum_j \lambda_j \geq \gamma$ (soglia di varianza, tipicamente 0.9-0.95).
5. **Proietta**: $Z = U_k^\top X \in \mathbb{R}^{k \times n}$.
6. (Opzionale) **Ricostruisci**: $\tilde X = U_k Z$.

## Connessione con la SVD

Se $X = U \Sigma V^\top$ allora $X X^\top = U \Sigma^2 U^\top$. Le componenti principali sono i vettori singolari di $X$; gli autovalori sono $\sigma_i^2$. Calcolare la PCA via [[Singular Value Decomposition|SVD]] è numericamente più stabile che diagonalizzare $C$.

## Modello generativo

Una volta stimato $W = U_k$, si possono generare nuovi dati: $z_{\text{new}} \in \mathbb{R}^k \mapsto x_{\text{new}} = W z_{\text{new}}$.

## Confronto con la regressione lineare

Nella regressione l'errore si misura **lungo l'asse $y$** (asse prefissato); nella PCA l'errore è misurato **ortogonalmente** al sottospazio scelto — questo cambia drasticamente la soluzione anche su dati uguali.

## Collegamenti

- Strumento spettrale sottostante: [[Singular Value Decomposition]]
- Massimizzazione spettrale: [[Quoziente di Rayleigh]]
- Calcolo iterativo: [[Power iteration]]
- Alternative non lineari: [[Multidimensional Scaling]], [[t-SNE]]
- Mitiga: [[Curse of dimensionality]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§6.1, 6.4, pp. 18-22)
