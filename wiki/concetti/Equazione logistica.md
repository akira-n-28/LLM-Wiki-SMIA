---
tipo: concetto
titolo: Equazione logistica
tag: [probabilità, processi-stocastici, dinamica, biologia-matematica]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-06
---

# Equazione logistica

Equazione differenziale ordinaria che modella la **crescita di una popolazione** con risorse limitate:

$$
\frac{dN}{dt} = r N \left(1 - \frac{N}{K}\right)
$$

con $r > 0$ tasso di crescita intrinseco e $K > 0$ **capacità portante** (carrying capacity) dell'ambiente.

## Soluzione esplicita

Separando le variabili:

$$
N(t) = \frac{K}{1 + \left(\frac{K}{N_0} - 1\right) e^{-rt}}
$$

con $N_0 = N(0)$.

Comportamento qualitativo:
- **Per $N \ll K$**: $\dot N \approx rN$, crescita esponenziale.
- **Per $N \to K$**: $\dot N \to 0$, saturazione asintotica.
- **Punti di equilibrio**: $N^* = 0$ (instabile) e $N^* = K$ (stabile asintoticamente).

## Connessione con i processi di nascita e morte

Nei [[Processo di nascita e morte|processi di nascita e morte]] stocastici con tassi:
$$
\lambda_n = (a - b n) n, \qquad \mu_n = c n
$$
(crescita logistica per la nascita, morte lineare), il **valore atteso** $E[N_t]$ soddisfa **approssimativamente** l'equazione logistica deterministica nel limite di popolazione grande:
$$
\frac{d E[N_t]}{dt} \approx r\, E[N_t]\!\left(1 - \frac{E[N_t]}{K}\right)
$$
con $r = a - c$ e $K = (a-c)/b$.

Questo è un **limite di scala**: la stocasticità diventa trascurabile nel limite termodinamico ($N \to \infty$), e la dinamica deterministica emerge dalle equazioni del bilancio.

## Confronto con la crescita esponenziale

La crescita esponenziale $\dot N = rN$ corrisponde al **processo di Yule** (puro nascita), valido finché le risorse sono illimitate. L'equazione logistica corregge per **competizione intra-specifica**: il termine $-rN^2/K$ rappresenta morti dovute a saturazione.

## Generalizzazioni e modelli affini

- **Lotka-Volterra** (preda-predatore): sistema accoppiato $\dot x = ax - bxy$, $\dot y = -cy + dxy$.
- **Equazione di Allee** $\dot N = rN(1 - N/K)(N/A - 1)$ — soglia $A$ sotto cui la popolazione si estingue.
- **Equazione SIR** in epidemiologia: $\dot S = -\beta SI$, $\dot I = \beta SI - \gamma I$, $\dot R = \gamma I$.
- **Funzione sigmoide** in [[Regressione logistica]]: stessa forma matematica, contesto diverso (probabilità invece di densità di popolazione).

## Connessioni con altri corsi

- [[Modelli Matematici per la Fisica I]]: ODE non lineari, [[Stabilità di un punto di equilibrio]] (Lyapunov), piano delle fasi.
- [[Processi Stocastici]]: limite continuo di processi di nascita e morte con feedback.
- [[Machine Learning]]: la [[Funzione sigmoide]] è la soluzione di $\dot y = y(1-y)$, equazione logistica normalizzata.

## Persone

- **Pierre-François Verhulst** (1838): introduzione del modello come correzione alla crescita malthusiana.
- **Lotka** e **Volterra** (1925-1926): sistemi preda-predatore.

## Fonti

- [[Dispense Processi Stocastici — Galletti]] (§5, equazione logistica come limite)
