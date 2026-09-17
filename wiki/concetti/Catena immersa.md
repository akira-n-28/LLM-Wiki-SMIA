---
tipo: concetto
titolo: Catena immersa
aliases: ["Embedded chain", "Catena scheletro"]
tag: [probabilità, processi-stocastici, catene-continue]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-06
---

# Catena immersa (embedded chain)

Per una [[Catena di Markov]] a tempo continuo $\{X_t\}$ con [[Generatore infinitesimale]] $Q$, la **catena immersa** $\{Y_n\}$ è la sequenza degli stati visitati ai tempi di salto, ignorando la durata della permanenza in ciascuno.

## Costruzione

Sia $\tau_n$ l'$n$-esimo istante di salto del processo continuo. Definisci:

$$
Y_n := X_{\tau_n}
$$

cioè $Y_n$ è lo stato in cui $X$ entra al salto $n$-esimo. La sequenza $\{Y_n\}$ è una **catena di Markov a tempo discreto** — la *struttura combinatoria* del processo continuo, separata dalla *cinetica temporale*.

## Matrice di transizione della catena immersa

Date le entrate del generatore $Q$:

$$
\Pi_{ij} = \begin{cases} \dfrac{Q_{ij}}{|Q_{ii}|} = \dfrac{Q_{ij}}{-Q_{ii}} & \text{se } i \neq j \\ 0 & \text{se } i = j \end{cases}
$$

Cioè: dato che lasci $i$, vai in $j$ con probabilità proporzionale al tasso $Q_{ij}$. La diagonale è zero perché un salto cambia sempre stato.

## Decomposizione del processo continuo

Un processo di Markov continuo si scompone in due ingredienti **indipendenti tra loro**:

1. **Catena immersa $\{Y_n\}$** — quale stato visita dopo (struttura).
2. **Tempi di permanenza $\{S_n\}$** — quanto rimane in $Y_n$. Sono $S_n \mid Y_n = i \sim \mathrm{Exp}(|Q_{ii}|)$ indipendentemente.

Da qui:
$$
X_t = Y_n \quad \text{per } \tau_n \leq t < \tau_{n+1}, \qquad \tau_{n+1} - \tau_n = S_n
$$

Il processo continuo è "guidato" dal moto della catena immersa, "ritmato" dalle esponenziali.

## Esempio: [[Processo di Poisson (continuo)]]

Generatore $Q_{ii} = -\lambda$, $Q_{i,i+1} = \lambda$. La catena immersa è deterministica: $Y_n = n$ (sale di 1 ogni salto). I tempi di permanenza sono $\mathrm{Exp}(\lambda)$ i.i.d. Esempio limite: tutta la struttura è nel timing, niente nello "scheletro".

## Esempio: [[Processo di nascita e morte]]

Per una catena di nascita e morte con tassi $\lambda_i$ (nascita da $i$) e $\mu_i$ (morte da $i$):

$$
\Pi_{i, i+1} = \frac{\lambda_i}{\lambda_i + \mu_i}, \qquad \Pi_{i, i-1} = \frac{\mu_i}{\lambda_i + \mu_i}
$$

La catena immersa è una **passeggiata aleatoria** (con probabilità di transizione che dipende dallo stato), e il processo continuo è la stessa passeggiata "rallentata" dai tempi esponenziali.

## Distribuzione stazionaria: continua vs discreta

**Attenzione**: la stazionaria della catena immersa $\Pi$ **non è** la stazionaria $\pi$ del processo continuo!

- $\pi$ è quella della catena continua: $\pi Q = 0$.
- $\Pi$-stazionaria pondera in base alla **frequenza dei salti**, non al tempo trascorso.

Relazione:
$$
\pi_i = \frac{\Pi^*_i / |Q_{ii}|}{\sum_j \Pi^*_j / |Q_{jj}|}
$$
dove $\Pi^*$ è la stazionaria della catena immersa. Più tempo si rimane in uno stato (cioè $|Q_{ii}|$ piccolo), più peso ha nella stazionaria continua.

## Quando usare la catena immersa

- **Simulazione efficiente** del processo continuo: simula la catena immersa (discreta) + i tempi (esponenziali).
- **Studio della ricorrenza/transienza**: dipende solo dalla catena immersa.
- **Calcoli di probabilità di assorbimento**: stessa risposta nel discreto e nel continuo.
- **Riduzione di dimensione**: alcune proprietà si analizzano meglio nello scheletro.

## Connessioni

- Genera: [[Catena di Markov]] (discreta) dalla controparte continua.
- Decompone: [[Processo di nascita e morte]], [[Processo di Poisson (continuo)]].
- Strumento per: [[Generatore infinitesimale]] (lega struttura + tempi).
- [[Distribuzione esponenziale]]: ritmica della catena.

## Fonti

- [[Dispense Processi Stocastici — Galletti]] (§5, struttura dei processi a tempo continuo)
