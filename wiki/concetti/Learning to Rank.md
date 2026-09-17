---
tipo: concetto
titolo: Learning to Rank
tag: [ml, information-retrieval]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Learning to Rank (LeToR)

**Obiettivo:** data una query $q$ e un insieme di documenti $\{d\}$, apprendere una funzione che ordini i documenti per rilevanza rispetto a $q$. È un problema di *ranking/ordinal*, non mera classificazione.

## Segnale di base

Un baseline è la **cosine similarity** tra vettori TF-IDF di query e documento:

$$
\cos(q, d) = \frac{\sum_i q_i d_i}{\|q\| \cdot \|d\|}
$$

In pratica si combinano molte feature (click, posizione dei termini, tempo/localizzazione, ecc.).

## Famiglie di metodi

**Pointwise** — apprende uno score scalare per ogni coppia $(q_i, d_j)$, poi ordina per score. Equivale a una regressione/classificazione standard.

**Pairwise** — apprende una preferenza tra due documenti della stessa query:
$$
(q_i, d_j, d_k) \mapsto y_{ijk} \in \{-1, +1\}
$$

**Listwise** — ottimizza direttamente l'ordine dell'intera lista per una query (es. massimizzare NDCG).

## RankNet (pairwise probabilistico)

Dato uno score $s(q, d) \in \mathbb{R}$, si modella la probabilità di ordine corretto con una sigmoide:
$$
P_{ij} = \sigma(\sigma_0 (s_i - s_j)), \quad \sigma(x) = \frac{1}{1+e^{-x}}
$$

La loss è una cross-entropy sulle coppie. Il **gradiente** (detto *lambda*):
$$
\lambda_{ij} = \frac{\partial C}{\partial s_i} = -\frac{\sigma_0}{1 + e^{\sigma_0(s_i - s_j)}}
$$

spinge $s_i$ verso l'alto e $s_j$ verso il basso quando $r_i > r_j$.

## LambdaRank

RankNet pesa tutte le coppie allo stesso modo, ma [[Metriche di ranking|NDCG]] dipende dalla posizione in lista. **LambdaRank** pesa i gradienti in base all'impatto sulla metrica:

$$
\lambda^{(\lambda)}_{ij} = \lambda_{ij} \cdot |\Delta\text{NDCG}_{ij}|
$$

dove $|\Delta\text{NDCG}_{ij}|$ è la variazione di NDCG se si scambiano le posizioni di $d_i$ e $d_j$. Avvicina l'ottimizzazione direttamente alla NDCG.

## Connessione con Gradient Boosting

In pratica LambdaRank si implementa spesso con [[Gradient Boosting]] decision trees (LambdaMART), che è lo stato dell'arte per il ranking su dati tabulari.

## Connessione con Bag of Words / TF-IDF

I segnali di base per il ranking (TF-IDF, cosine similarity) derivano dalla rappresentazione testuale tramite [[Bag of Words e TF-IDF]].

## Collegamenti

- Metrica target: [[Metriche di ranking]] (NDCG)
- Implementazione pratica: [[Gradient Boosting]]
- Rappresentazione documenti: [[Bag of Words e TF-IDF]]
- Contesto più ampio: [[Sistemi di raccomandazione]]
- Discusso in: [[Informatica per il Machine Learning]] (§6.5)

## Fonti

- [[Dispense InfML — Galletti]] (§6.5, pp. 22-24)
