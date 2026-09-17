---
tipo: concetto
titolo: Entropia di Shannon
tag: [mmf, teoria-dell-informazione, probabilità]
cluster: fisica
fonti: 1
ultima-modifica: 2026-05-06
---

# Entropia di Shannon

Introdotta da Shannon (1948) per formalizzare la **quantità di informazione** in un messaggio. Data $X$ con distribuzione $\{p_i\}$ su $\Omega_X$ di cardinalità $L$:

$$H(X) = -\sum_{x \in \Omega_X} p(x)\log_2 p(x) = \mathbb{E}\!\left[\log_2 \frac{1}{p(X)}\right]$$

## Proprietà fondamentali

| Proprietà | Enunciato |
|---|---|
| Non negatività | $H(X) \geq 0$ |
| Certezza | $H(X) = 0 \Leftrightarrow \exists x: p(x) = 1$ |
| Massimo | $H(X) \leq \log_2 L$ |
| Massimo uniforme | $H(X) = \log_2 L \Leftrightarrow p(x) = 1/L\ \forall x$ |

L'entropia è massima in stato di massima incertezza (distribuzione uniforme), zero in stato di massima certezza. Si prova via moltiplicatori di Lagrange massimizzando $H$ con vincolo $\sum p_i = 1$.

**Interpretazione:** $H(X)$ è il numero medio di bit necessari per codificare un messaggio. Ottimale rispetto al codice di Huffman (cfr. [[Algoritmo di Huffman]]).

## Entropia correlata e informazione mutua

Per due variabili $X, Y$ congiunte:

$$H(X,Y) = -\sum_{x,y} p(x,y)\log_2 p(x,y)$$

**Proprietà di subadditività:**

$$H(X,Y) \leq H(X) + H(Y)$$

con uguaglianza sse $X \perp Y$ (i.e. $p(x,y) = p(x)p(y)$).

**Informazione mutua:**

$$I(X;Y) = H(X) + H(Y) - H(X,Y) = \sum_{x,y} p(x,y)\log_2\frac{p(x,y)}{p(x)p(y)} \geq 0$$

Misura quanto $X$ e $Y$ si "informano" a vicenda. $I(X;Y) = 0$ sse $X \perp Y$.

## Divergenza di Kullback-Leibler

$$D_{KL}(p\|q) = \sum_x p(x)\log\frac{p(x)}{q(x)} \geq 0$$

**Proprietà:** $D_{KL}(p\|q) = 0 \Leftrightarrow p = q$; non è simmetrica. Si prova con $\log x \leq x - 1$.

Legame con info mutua: $I(X;Y) = D_{KL}(p(x,y)\|p(x)p(y))/\log 2$.

(Vedi anche [[Divergenza di Kullback-Leibler]] per l'uso nel contesto ML.)

## Entropia di Gibbs

In fisica si usa il logaritmo naturale:

$$S(X) = -\sum_x p_x\log p_x = \frac{H(X)}{\log 2} \in [0, \log L]$$

La differenza è solo nella base del logaritmo (bit vs. nats).

## Connessioni

- Uso per codifica ottimale: [[Algoritmo di Huffman]]
- Massimizzazione vincolata: [[Principio di massima entropia]]
- In ML: [[Divergenza di Kullback-Leibler]], [[Cross-entropy]]
- Corsi: [[Modelli Matematici per la Fisica II]]

## Fonti

- [[Dispense MMFII — Galletti]] (§2, pp. 19-26)
