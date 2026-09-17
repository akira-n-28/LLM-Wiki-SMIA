---
tipo: concetto
titolo: Problema di ottimizzazione
tag: [ottimizzazione, matematica-applicata]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Problema di ottimizzazione

**Forma standard:**

$$
\min_{x \in S} f(x)
$$

dove $f: \mathbb{R}^n \to \mathbb{R}$ è la **funzione obiettivo**, $S \subseteq \mathbb{R}^n$ è l'**insieme ammissibile** e $x \in \mathbb{R}^n$ è il **vettore delle variabili di decisione**. Un problema di massimo si riconduce a minimizzare $-f(x)$.

## Classificazione

```
Ottimizzazione
├── Infinito-dimensionale (spazi di funzioni)
└── Finito-dimensionale
    ├── Discreta
    │   ├── Combinatoria
    │   └── Su grafi
    └── Continua
        ├── Lineare
        └── Non lineare
            ├── Convessa
            └── Non convessa
                ├── Differenziabile
                └── Non differenziabile
```

## Minimo globale e locale

**Globale**: $x^* \in S$ con $f(x^*) \leq f(x) \;\forall x \in S$.

**Locale**: $\exists B(x^*, \rho)$ tale che $f(x^*) \leq f(x) \;\forall x \in B(x^*, \rho) \cap S$.

Ogni minimo globale è locale; il viceversa vale solo se $f$ è convessa su $S$ convesso (→ [[Convessità]]).

## Esempi canonici

**Problema di assegnamento** (LP): $N$ ingegneri, $N$ progetti, $t_{ij}$ tempo di addestramento.
$$
\min \sum_{i,j} t_{ij} x_{ij}, \quad \sum_j x_{ij}=1\;\forall i, \quad \sum_i x_{ij}=1\;\forall j, \quad x_{ij} \geq 0
$$
Equivalente al problema con $x_{ij} \in \{0,1\}$ (per struttura totalmente unimodulare).

**Knapsack** (combinatorio): $\max \sum c_i x_i$ con $\sum a_i x_i \leq D$, $x_i \in \{0,1\}$.

**Addestramento reti neurali** (non lineare, non convesso):
$$
\min_{w \in \mathbb{R}^n} E(w) = \sum_{p=1}^P \bigl(y^p - y(u^p, w)\bigr)^2
$$

**Clustering**: $\min \sum_j \sum_p \delta_{pj} \|u^p - z_j\|$ con $\sum_j \delta_{pj}=1$, $\delta_{pj} \in \{0,1\}$.

## Condizioni di esistenza

- **Teorema di Weierstrass**: $S$ compatto e non vuoto, $f$ continua $\Rightarrow$ minimo e massimo globali esistono.
- **Caso non vincolato**: basta che esista un insieme di livello $L_\alpha^f = \{x: f(x) \leq \alpha\}$ compatto. Equivalente a $f$ **coerciva**: $\|x^k\| \to \infty \Rightarrow f(x^k) \to \infty$.
- $f(x) = \frac12 x^T Q x + c^T x$ coerciva $\Leftrightarrow$ $Q$ definita positiva.

## Algoritmi: schema generale

$$
x_{k+1} = x_k + s_k, \quad k = 0, 1, \ldots
$$

Le questioni fondamentali sono: (1) esistenza di punti limite di $\{x_k\}$, (2) convergenza a punti stazionari, (3) rapidità di convergenza.

**Rapidità di convergenza** di $\{x_k\} \to \bar{x}$:
- Lineare: $\|x_{k+1} - \bar{x}\| \leq \sigma \|x_k - \bar{x}\|$, $\sigma \in (0,1)$
- Quadratica: $\|x_{k+1} - \bar{x}\| \leq c \|x_k - \bar{x}\|^2$
- Superlineare: $\lim_{k\to\infty} \|x_{k+1}-\bar{x}\|/\|x_k-\bar{x}\| = 0$

## Collegamento con i corsi

- [[Ottimizzazione]]: corso completo su questo tema.
- [[Apprendimento statistico]] ([[Matematica per il Machine Learning]]): [[ERM]] è un problema di ottimizzazione.
- [[Machine Learning]]: ogni modello parametrico si addestra ottimizzando una funzione di perdita.

## Fonti

- [[Dispense Ottimizzazione — Galletti]] (§1.1, §2, pp. 2-24)
