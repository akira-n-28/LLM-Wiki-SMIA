---
tipo: concetto
titolo: Riduzione della varianza
tag: [probabilità, statistica-computazionale]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Tecniche di riduzione della varianza

Lo stimatore Monte Carlo grezzo `ȳ_N = (1/N) Σ y_i` ha varianza `Var[Y]/N`. Ridurre l'errore di un fattore 10 richiede 100× più campioni. Le tecniche di riduzione della varianza agiscono invece sul **numeratore `Var[Y]`**, producendo stimatori più efficienti a parità di costo computazionale.

## Panoramica delle tecniche

| Tecnica | Idea |
|---|---|
| **Variabili di controllo** | Sfrutta la correlazione con una v.a. a valore atteso noto |
| **Variabili antitetiche** | Accoppia campioni correlati negativamente |
| **[[Importance Sampling]]** | Ricampiona da una distribuzione più efficiente |
| **MC condizionato** | Condiziona su variabili ausiliarie per ridurre la variabilità |
| **Campionamento stratificato** | Divide il dominio in strati, campiona separatamente |

## Variabili di controllo

**Definizione.** Sia `Y` la v.a. di interesse (`µ = E[Y]`) e `Ỹ` una **variabile di controllo**: calcolata dallo stesso esperimento, con `µ̃ = E[Ỹ]` **noto analiticamente** e correlata con `Y`.

Lo stimatore con variabile di controllo è:

$$
\hat\mu^{(C)} = \frac{1}{N}\sum_{k=1}^N [y_k - \alpha(\tilde y_k - \tilde\mu)]
$$

**Non distorto** per ogni `α ∈ ℝ` (il termine in `Ỹ` ha valore atteso zero).

### Scelta ottimale di α

La varianza è minimizzata da:

$$
\alpha^* = \frac{\mathrm{Cov}(Y, \tilde Y)}{\mathrm{Var}[\tilde Y]} = \rho_{Y,\tilde Y}\sqrt{\frac{\mathrm{Var}[Y]}{\mathrm{Var}[\tilde Y]}}
$$

e la varianza ridotta vale:

$$
\mathrm{Var}[\hat\mu^{(C)}] = \frac{\mathrm{Var}[Y]}{N}(1 - \rho_{Y,\tilde Y}^2)
$$

Il fattore di riduzione `(1-ρ²) ∈ [0,1]`:
- `|ρ| = 1` → varianza nulla (stima perfetta)
- `ρ = 0` → nessun guadagno (torna al MC grezzo)

**In pratica**: `α*` non è noto a priori, ma si stima dagli stessi campioni MC usando gli stimatori empirici di covarianza e varianza.

## Esempio: integrale 3D

$$
\mu = \iiint_{\mathbb{R}^3} \sqrt{|x_1+x_2+x_3|}\,(2\pi)^{3/2}\, e^{-(x_1^2+x_2^2+x_3^2)/2}\,dx_1\,dx_2\,dx_3 = \mathbb{E}[Y]
$$

con `Y = √|X₁+X₂+X₃| · (2π)^{3/2}`, `X_i ∼ N(0,1)` i.i.d.

Variabile di controllo: `Ỹ = X₁²+X₂²+X₃²` con `µ̃ = E[X_i²] · 3 = 3` (nota).
Alta correlazione con `Y` perché entrambe dipendono da `‖X‖²`.

## Connessione con Importance Sampling

[[Importance Sampling]] può essere visto come una tecnica di riduzione della varianza in cui si modifica la distribuzione di campionamento `f → g` invece di correggere i campioni. Le due tecniche sono complementari.

## Connessione con l'MC grezzo

La varianza del MC grezzo `Var[Y]/N` è il caso `ρ = 0` della formula sopra. Qualsiasi variabile di controllo con correlazione non nulla dà un miglioramento.

## Connessione con Processi Stocastici

L'esempio del cammino aleatorio su grafo (stima di `E[R]/E[C]`) usa Bootstrap per stimare la varianza; in alternativa si potrebbero usare variabili di controllo costruite sulle proprietà della catena (es. valore atteso del tempo di ciclo).

## Limitazione

`α*` dipende dalla covarianza teorica (spesso ignota). La stima empirica di `α*` dai dati introduce un bias, trascurabile per `N` grande.

## Collegamenti

- Categoria: [[Metodi Monte Carlo]]
- Tecnica affine: [[Importance Sampling]]
- Usata per: ridurre l'errore nella stima di integrali complessi

## Fonti

- [[Dispense MatML — Galletti]] (§3.12, teorema 3.1, esempio 3.12, pp. 59-61)
