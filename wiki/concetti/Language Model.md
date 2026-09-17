---
tipo: concetto
titolo: Language Model
tag: [nlp, probabilità, ml]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# Language Model (LM)

Un **Language Model** definisce una distribuzione di probabilità su sequenze di token:
$$p(s) = p(t_1, t_2, \ldots, t_n)$$

Misura la verosimiglianza di una sequenza e si usa per raccogliere informazioni, speech recognition, spell checking, traduzione, generazione di testo, information retrieval.

## K-Gram Language Model

L'approccio naive (frequenza relativa dell'intera frase) è impraticabile per la scarsità dei dati. Si sfrutta invece la **regola della catena** con un'**assunzione di Markov di ordine $k$**: la probabilità di un token dipende solo dai $k-1$ precedenti:

$$p(t_m | t_{m-1}, \ldots, t_1) \approx p(t_m | t_{m-1}, \ldots, t_{m-k+1})$$

**Bigram** ($k=2$):
$$p(t_m | t_{m-1}) = \frac{\text{count}(t_{m-1}, t_m)}{\text{count}(t_{m-1})}$$

### Smoothing

Per evitare probabilità zero su sequenze mai viste: si aggiunge una piccola quantità $\alpha$ a tutti i conteggi (Lidstone smoothing):

$$p_\text{smooth}(w_m | w_{m-1}) = \frac{\text{count}(w_{m-1}, w_m) + \alpha}{\sum_{w'} \text{count}(w_{m-1}, w') + \alpha |V|}$$

- $\alpha = 1$: Laplace smoothing
- $\alpha = 0.5$: Jeffreys-Perks

### OOV (Out of Vocabulary)

Parole non presenti nel vocabolario vengono mappate a `<UNK>`, trattato come una parola reale con proprie probabilità apprese.

## LM in Information Retrieval

Ogni documento $d$ è modellato come un LM $M_d$. Il ranking per una query $q$ si basa su:

$$P(d|q) \propto P(q|d) = \prod_t P(t|M_d)$$

Il documento viene visto come un **generative model**: la probabilità che il suo LM generi le parole della query.

## Neural Language Model

L'approccio neurale tratta la predizione della parola successiva come classificazione discriminativa:

$$P(w_i | C_j) = \frac{e^{\theta_{w_i} \cdot \theta_{C_j}}}{\sum_{w'} e^{\theta_{w'} \cdot \theta_{C_j}}} = \text{softmax}(\ldots)$$

La softmax sull'intero vocabolario è costosa: $O(|V|)$. Word2Vec lo aggira con Negative Sampling (cfr. [[Word Embedding]]).

## Modelli autoregressivi

I LM neurali moderni (RNN, Transformer) sono **autoregressivi**: generano un token alla volta, condizionando ogni predizione sui precedenti:

$$P(x_1, \ldots, x_T) = \prod_{t=1}^T P(x_t | x_1, \ldots, x_{t-1})$$

cfr. [[Recurrent Neural Network]], [[Transformer]].

## Teacher Forcing

Durante il training, invece di usare l'output generato come input successivo, si usa il **ground truth** corretto. Accelera la convergenza. All'inferenza non è disponibile → possibile exposure bias.

## ELMo

ELMo (Embeddings from Language Models) genera embedding **contestuali** tramite una biLSTM bidirezionale. La rappresentazione di ogni parola è una combinazione pesata delle rappresentazioni di tutti i layer: $\text{ELMo}_k = \gamma \sum_j s_j h_{k,j}$.

## Connessione con BERT

BERT (cfr. [[BERT]]) usa un transformer encoder pre-addestrato con Masked Language Model (MLM) invece della predizione sinistra-destra classica.

## Collegamenti

- Rappresentazione classica: [[Bag of Words e TF-IDF]]
- Embedding: [[Word Embedding]]
- Architettura neurale: [[Recurrent Neural Network]], [[Transformer]], [[BERT]]
- Ranking con LM: [[Learning to Rank]]
- Discusso in: [[Informatica per il Machine Learning]] (§11, pp. 36-42)

## Fonti

- [[Dispense InfML — Galletti]] (§11, pp. 36-42)
