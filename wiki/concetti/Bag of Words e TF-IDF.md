---
tipo: concetto
titolo: Bag of Words e TF-IDF
tag: [nlp, information-retrieval, rappresentazione]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# Bag of Words e TF-IDF

Tecniche di rappresentazione vettoriale di testi. Prerequisito classico per [[Sentiment Analysis]], [[Learning to Rank]] e retrieval su testo.

## Bag of Words (BoW)

Dato un vocabolario $V = \{w_1, \ldots, w_{|V|}\}$, ogni documento/frase è rappresentato come un vettore di dimensione $|V|$:

- **Binario:** ogni dimensione è 1 se la parola è presente, 0 altrimenti.
- **Contatore:** ogni dimensione conta le occorrenze della parola.

**Esempio:** $V = \{\text{"a","cat","dog","file","string"}\}$, frase "A string file":
$$\text{one-hot-encoding}(t) = [1, 0, 0, 1, 1]^\top$$

**Limite:** la dimensionalità esplode linearmente con $|V|$ (vocabolari realistici: $|V| \approx 10^5$); l'ordine delle parole è perso.

## TF-IDF (Term Frequency – Inverse Document Frequency)

Pesa le parole in base alla loro importanza discriminativa. Ogni dimensione del vettore documento vale:

$$
\text{TF-IDF}(t, d) = \text{TF}(t, d) \times \text{IDF}(t)
$$

- **TF:** quante volte il termine $t$ appare nel documento $d$.
- **IDF:** misura della rarità del termine nel corpus:
$$\text{IDF}(t) = \log \frac{\text{Documenti totali}}{\text{Documenti contenenti } t}$$

Parole molto frequenti in tutti i documenti (es. "il", "di") hanno IDF basso e quindi peso ridotto. Parole rare e specifiche hanno IDF alto.

## Hashing Trick (Feature Hashing)

Risolve il problema della dimensionalità senza mantenere un dizionario globale: si usa una funzione di hash $h(\cdot)$ per mappare ogni token in un indice di un vettore a dimensione fissa $D$ (scelta a priori):

$$\text{index} = h(\text{token}) \mod D$$

- **Vantaggi:** memoria $O(D)$ costante; stateless (utile per streaming).
- **Svantaggi:** collisioni (parole diverse → stesso bucket); irreversibile.

## Limiti della rappresentazione BoW

- Non cattura la similarità semantica (parole diverse sono ortogonali).
- Perde l'ordine delle parole.

Questi limiti motivano i [[Word Embedding]] (rappresentazioni dense) e infine i [[Language Model]] neurali.

## Connessione con il ranking

TF-IDF è il segnale di base per il [[Learning to Rank]]: la cosine similarity tra vettori TF-IDF di query e documento è il baseline classico di relevance score.

## Connessione con Word2Vec

In CBOW il nome "Bag of Words" indica che l'ordine non conta: si media sulle parole di contesto. Vedi [[Word Embedding]].

## Collegamenti

- Applicazione: [[Sentiment Analysis]], [[Learning to Rank]]
- Superate da: [[Word Embedding]]
- Discusso in: [[Informatica per il Machine Learning]] (§10, pp. 35-36)

## Fonti

- [[Dispense InfML — Galletti]] (§10, pp. 35-36)
