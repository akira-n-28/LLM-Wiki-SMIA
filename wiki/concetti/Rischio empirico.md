---
tipo: concetto
titolo: Rischio empirico
tag: [ml, statistica, fondamenti]
cluster: ml
fonti: 1
ultima-modifica: 2026-04-30
---

# Rischio empirico (Training Loss)

Media della [[Funzione di perdita]] calcolata sui dati di un training set `T = {(X₁,Y₁), …, (Xₙ,Yₙ)}`:

$$
\ell_T(g) := \frac{1}{n} \sum_{i=1}^{n} L(Y_i, g(X_i))
$$

Approssimazione computabile del [[Rischio teorico]] (che richiederebbe la distribuzione vera `P`).

## Proprietà come stimatore

Distinzione cruciale (Oss. 2.2 dispense):

- Se `g` è **fissata a priori** (indipendente dai dati), allora `ℓ_T(g)` è uno **stimatore non distorto** di `ℓ(g)` (linearità del valore atteso).
- Se `g = g_T` è il **learner addestrato sui dati**, allora `ℓ_T(g_T)` è **fortemente distorto e ottimistico**: avendo l'algoritmo minimizzato l'errore proprio su `T`, sottostima sistematicamente il rischio reale di generalizzazione.

Questa distorsione si quantifica come [[Ottimismo]].

## Bias e ottimalità

Avere uno stimatore non distorto **non equivale** ad averne uno ottimale: imporre l'assenza di bias restringe lo spazio di ricerca. Accettare un po' di bias può ridurre drasticamente la varianza ⇒ [[Bias-Variance trade-off]].

## Empirical Risk Minimization

Il principio cardine è scegliere il modello che minimizza `ℓ_T` su una classe `G`:

$$
g_T^G = \arg\min_{g \in G} \ell_T(g)
$$

Vedi [[ERM]].

## Collegamenti

- Approssima: [[Rischio teorico]]
- Distorsione misurata da: [[Ottimismo]], [[Rischio in-sample]]
- Stima migliore tramite: [[Cross-validation]]

## Fonti

- [[Dispense MatML — Galletti]] (def. 2.2, oss. 2.2-2.3, pp. 12-13)
