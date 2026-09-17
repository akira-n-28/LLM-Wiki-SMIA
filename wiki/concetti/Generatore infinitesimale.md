---
tipo: concetto
titolo: Generatore infinitesimale
tag: [probabilità, processi-stocastici, catene-continue]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Generatore infinitesimale

Per una [[Catena di Markov]] a **tempo continuo** con matrice di transizione `P(t)`, il **generatore infinitesimale** `Q` è definito come:

$$
Q := P'(0) = \lim_{h \to 0} \frac{P(h) - I}{h}
$$

## Proprietà di Q

- `Qᵢᵢ < 0` (probabilità di uscita dallo stato `i`)
- `Qᵢⱼ ≥ 0` per `i ≠ j` (tassi di salto)
- Somma di ogni riga = 0: `Σⱼ Qᵢⱼ = 0`, ovvero `Qᵢᵢ = -Σⱼ≠ᵢ Qᵢⱼ`

## Equazione esponenziale di matrice

La matrice di transizione al tempo `t` è:

$$
P(t) = e^{Qt} = \sum_{n=0}^\infty \frac{(Qt)^n}{n!} = I + Qt + \frac{Q^2 t^2}{2!} + \cdots
$$

Le matrici `P(t)` formano un **semigruppo**: `P(t)P(s) = P(t+s)`, `P(0) = I`.

## Equazioni di Kolmogorov

- **In avanti**: `P'(t) = P(t)Q` — descrive l'evoluzione forward della distribuzione
- **Indietro**: `P'(t) = QP(t)` — descrive l'evoluzione backward

Per la distribuzione `νₜ = ν₀ P(t)`:

$$
\frac{d\nu_t}{dt} = \nu_t Q
$$

## Esempio: catena a due stati

Per stati `{0, 1}` con tassi `α` (da 0 a 1) e `β` (da 1 a 0):

$$
Q = \begin{pmatrix} -\alpha & \alpha \\ \beta & -\beta \end{pmatrix}, \quad P(\Delta t) \approx I + Q\Delta t = \begin{pmatrix} 1-\alpha\Delta t & \alpha\Delta t \\ \beta\Delta t & 1-\beta\Delta t \end{pmatrix}
$$

La distribuzione stazionaria è `π = (β/(α+β), α/(α+β))`.

## Nota: esponenziale di matrice

Attenzione: `e^{A+B} = e^A e^B` vale **solo se** `A` e `B` commutano (`AB = BA`). In generale `(A+B)² = A² + AB + BA + B²` con `AB ≠ BA`.

## Connessione con i corsi

- [[Processi Stocastici]]: §5.2, nucleo della teoria a tempo continuo.
- [[Processo di nascita e morte]]: l'esempio principale di catena con generatore infinitesimale tridiagonale.
- [[Singular Value Decomposition]]: l'esponenziale di matrice si calcola efficacemente tramite diagonalizzazione `Q = VΛV⁻¹` → `e^{Qt} = Ve^{Λt}V⁻¹`.

## Fonti

- [[Dispense Processi Stocastici — Galletti]] (§5.2, pp. 21-23)
