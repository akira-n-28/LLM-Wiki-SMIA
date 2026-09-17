---
tipo: concetto
titolo: Metodo del corrispondente stocastico
tag: [ottimizzazione, statistica-computazionale]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Metodo del corrispondente stocastico (Sample Average Approximation)

Tecnica per minimizzare `S(λ) = E_f[S̃(λ, X)]` quando `S` non è accessibile in forma chiusa. L'idea: approssimazione `S` con la **media campionaria** su un campione fisso, trasformando il problema stocastico in uno **deterministico**.

## Procedura

1. Estrai **una volta per tutte** un campione `x_1, …, x_N ∼ f`.
2. Definisci il **corrispondente stocastico** di `S`:

$$
\hat S(\lambda) = \frac{1}{N}\sum_{i=1}^N \tilde S(\lambda, x_i)
$$

3. Minimizza `Ŝ(λ)` con tecniche di ottimizzazione **deterministica** (discesa del gradiente, Newton, …):

$$
\hat\lambda^* = \arg\min_\lambda \hat S(\lambda)
$$

## Proprietà di convergenza

Per la **Legge dei Grandi Numeri**: `Ŝ(λ) → S(λ)` quasi certamente per `N → ∞`, per ogni `λ` fissato.

Sotto ipotesi di regolarità, anche il minimizzatore converge:

$$
\hat\lambda^* \xrightarrow{N\to\infty} \lambda^*
$$

## Differenza chiave rispetto all'approssimazione stocastica

| | [[Approssimazione stocastica]] | Corrispondente stocastico |
|---|---|---|
| **Campioni** | Nuovi ad ogni iterazione | Fissati prima dell'ottimizzazione |
| **Problema** | Stocastico (cambia a ogni step) | Deterministico (una volta fissato il campione) |
| **Costo per step** | O(N_batch) | O(N) per la valutazione iniziale |
| **Ottimizzazione** | Gradiente rumoroso | Qualsiasi metodo deterministico |
| **Convergenza** | Asintotica in `t` | Asintotica in `N` |

## Esempio: ottimizzazione del parametro λ di IS

Nel [[Importance Sampling]], si vuole minimizzare:

$$
S(\lambda) = \mathbb{E}_f\!\left[\frac{H^2(X)\,f(X)}{g_\lambda(X)}\right]
$$

Il corrispondente stocastico è:

$$
\hat S(\lambda) = \frac{1}{N}\sum_{i=1}^N \frac{H^2(x_i)\,f(x_i)}{g_\lambda(x_i)}, \quad x_i \sim f
$$

Una volta fissati gli `x_i`, `Ŝ(λ)` è una funzione **deterministica** di `λ`, minimizzabile con gradient descent classico o metodi di secondo ordine.

## Vantaggi

- Usa algoritmi di ottimizzazione deterministica maturi e ben calibrati.
- Nessun hyper-parameter `β_t` (learning rate).
- Facile da diagnosticare: si può verificare la convergenza di `Ŝ(λ)` con strumenti standard.

## Svantaggi

- Il campione fisso introduce un **errore di approssimazione** fisso (non si migliora con più iterazioni, solo con `N` più grande).
- Per `d` grande e `N` moderato, la stima `Ŝ` può essere rumorosa.

## Connessione con la statistica

Il corrispondente stocastico è un'applicazione diretta del principio di **plug-in**: sostituire la distribuzione vera con la distribuzione empirica. Stesso principio del [[Bootstrap]].

## Connessione con i corsi SMIA

- [[Ottimizzazione]]: tutti i metodi del gradiente si applicano a `Ŝ` una volta fissato il campione.
- [[Machine Learning]]: il training su un dataset fisso è tecnicamente un corrispondente stocastico (minimizza la loss empirica invece di quella teorica → [[ERM]]).

## Note sul nome

Il metodo è noto anche come **Sample Average Approximation (SAA)** in programmazione stocastica, o semplicemente come **empirical risk minimization** in ML quando il campione è il training set.

## Connessione con ERM

La [[ERM]] (Empirical Risk Minimization) è un caso speciale del corrispondente stocastico: si minimizza il rischio empirico `ℓ_τ(g)` (corrispondente stocastico del rischio teorico `ℓ(g)`) sullo stesso training set fisso.

## Connessione con il Metodo Cross-Entropy

Nel [[Metodo Cross-Entropy]], l'aggiornamento di `v` tramite MLE sull'élite è un'applicazione del corrispondente stocastico applicato alla massimizzazione di `E_{f*}[log f(X|v)]`.

## Connessione con Bootstrap

[[Bootstrap]] e corrispondente stocastico usano entrambi la distribuzione empirica come surrogato di `f`. Bootstrap valuta la variabilità dello stimatore; SAA trova l'ottimo del corrispondente.

## Collegamenti

- Alternativa a: [[Approssimazione stocastica]]
- Usato in: [[ERM]], [[Importance Sampling]] (ottimizzazione di λ), [[Metodo Cross-Entropy]]
- Principio analogo: [[Bootstrap]] (plug-in empirico)

## Fonti

- [[Dispense MatML — Galletti]] (§3.15.2, pp. 65-66)
