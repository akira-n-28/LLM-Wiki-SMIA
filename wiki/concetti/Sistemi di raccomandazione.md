---
tipo: concetto
titolo: Sistemi di raccomandazione
tag: [ml, information-retrieval]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Sistemi di raccomandazione

**Obiettivo:** dato un insieme di utenti e oggetti (film, prodotti, articoli), ordinare gli oggetti per rilevanza o utilità per ciascun utente.

## Matrice utente-oggetto

Le interazioni si rappresentano come una matrice $R \in \mathbb{R}^{m \times n}$ (utenti × oggetti), dove $r_{ui}$ è la valutazione dell'utente $u$ sull'oggetto $i$. La matrice è **molto sparsa** (ogni utente interagisce con una piccola parte degli oggetti).

## Matrix Factorization

Per ridurre la dimensionalità e stimare i valori mancanti si fattorizza $R$ in due matrici di rango ridotto:

$$
R \approx QP
$$

dove:
- $Q \in \mathbb{R}^{m \times k}$ — rappresentazione latente degli utenti ($k \ll m$)
- $P \in \mathbb{R}^{k \times n}$ — rappresentazione latente degli oggetti

L'obiettivo è minimizzare l'errore di ricostruzione $\|R - QP\|$ sui rating osservati.

Questo equivale ad apprendere **embedding latenti** per utenti e oggetti: la similarità di embedding predice l'interesse.

## Connessione con SVD e ranking

La fattorizzazione è la stessa idea della [[Singular Value Decomposition|SVD]] (approssimazione a basso rango). Per la generazione delle raccomandazioni, si ordina poi per score $q_u \cdot p_i$ — un problema di [[Learning to Rank]].

## Approcci alternativi

- **Collaborative filtering** (basato sul comportamento di utenti simili)
- **Content-based filtering** (basato sulle caratteristiche degli oggetti)
- **Modelli neurali** (con embedding appresi da reti profonde)

## Collegamenti

- Tecnica sottostante: [[Singular Value Decomposition]], [[Principal Component Analysis]]
- Ordinamento dei risultati: [[Learning to Rank]], [[Metriche di ranking]]
- Rappresentazione: [[Word Embedding]] (stessa idea di embedding latenti)
- Discusso in: [[Informatica per il Machine Learning]] (§7)

## Fonti

- [[Dispense InfML — Galletti]] (§7, p. 24)
