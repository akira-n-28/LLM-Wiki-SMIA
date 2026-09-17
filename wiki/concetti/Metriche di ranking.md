---
tipo: concetto
titolo: Metriche di ranking
tag: [ml, information-retrieval, valutazione]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Metriche di ranking

Metriche per valutare la qualità di un *ordinamento* di documenti (o item) rispetto a una query. Differiscono dalle [[Metriche di classificazione]] perché penalizzano i documenti rilevanti relegati in fondo alla lista.

## Precision@k e Recall@k

Considerando solo i primi $k$ risultati:

$$
\text{Precision@}k = \frac{|\text{rilevanti tra i top-}k|}{k}, \quad \text{Recall@}k = \frac{|\text{rilevanti tra i top-}k|}{|\text{rilevanti nel corpus}|}
$$

**Bias applicativo:** se perdere un rilevante è grave (ricerca medica) → privilegiare recall; se l'utente legge solo i primi risultati → privilegiare precision.

## MRR (Mean Reciprocal Rank)

Quando basta trovare *almeno un* risultato rilevante il prima possibile:

$$
\text{MRR} = \frac{1}{N} \sum_{i=1}^N \frac{1}{R_i}
$$

dove $R_i$ è la posizione del *primo* documento rilevante per la query $i$.

**Limite:** ignora completamente la struttura dopo il primo rilevante.

## MAP (Mean Average Precision)

Tiene conto di *tutti* i documenti rilevanti. Per una query con $R$ rilevanti:

$$
\text{AP@}k = \frac{1}{\min(R,k)} \sum_{i=1}^k \text{Precision@}i \cdot \mathbf{1}[\text{doc}_i \text{ rilevante}]
$$

$$
\text{MAP} = \frac{1}{N} \sum_{j=1}^N \text{AP}_j
$$

Premia i rilevanti in cima. Assume rilevanza **binaria**.

## NDCG (Normalized Discounted Cumulative Gain)

Estende MAP a rilevanza **graduata** (es. scala 0–4) e applica uno sconto logaritmico per posizione:

$$
\text{DCG} = \sum_{i=1}^n \frac{2^{r_i} - 1}{\log_2(i+1)}, \quad \text{NDCG} = \frac{\text{DCG}}{\text{IDCG}}
$$

dove $r_i$ è la rilevanza del documento in posizione $i$, e IDCG è il DCG dell'ordinamento ideale (massimo possibile). È la metrica più usata nei sistemi di ricerca commerciali.

**Esempio discriminante:** due sistemi con lo stesso MRR = 1 (primo rilevante al rank 1) ma diversa qualità nelle posizioni successive → stesso MRR, NDCG diversi.

## Confronto

| Metrica | Rilevanza | Considera ordine dopo il 1° | Uso tipico |
|---|---|---|---|
| Precision@k | binaria | parziale | motori di ricerca |
| MRR | binaria | no | Q&A, navigazione |
| MAP | binaria | sì | IR standard |
| NDCG | graduata | sì | sistemi commerciali |

## Connessione con il Learning to Rank

NDCG è la metrica obiettivo di **LambdaRank** (vedi [[Learning to Rank]]).

## Collegamenti

- Metriche di classificazione classiche: [[Metriche di classificazione]]
- Ottimizzazione diretta: [[Learning to Rank]]
- Contesto di applicazione: [[Sistemi di raccomandazione]]
- Discusso in: [[Informatica per il Machine Learning]] (§5.1, §6.5)

## Fonti

- [[Dispense InfML — Galletti]] (§5.1, §6.5, pp. 16-24)
