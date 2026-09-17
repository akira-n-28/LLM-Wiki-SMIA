---
tipo: corso
titolo: Modelli Matematici per la Fisica II
docente: Francesco Zamponi
anno-accademico: 2024/2025
codice-breve: mmfII
ultima-modifica: 2026-05-06
tag: [fisica-matematica, probabilità, meccanica-statistica, smia]
---

# Modelli Matematici per la Fisica II

Corso di **Modelli Matematici per la Fisica II** tenuto dal prof. **Francesco Zamponi** nell'A.A. 2024/2025, SMIA, Sapienza. Focus: probabilità avanzata, entropia, meccanica statistica, modelli a spin.

## Programma

1. **Richiami di probabilità** (§1, pp. 1-18)
   - [[Funzione generatrice dei momenti]] — cumulanti, $K_X(t)=\log\mathbb{E}[e^{tX}]$, $\kappa_1=\mu$, $\kappa_2=\sigma^2$
   - Dimostrazione del TLC via cumulanti ($\kappa_l(\hat{S}_n)\to 0$ per $l\geq 3$)
   - [[Teoria delle grandi deviazioni]] — bound di Cramér $P(u_n\geq u)\leq e^{-n\Omega(u)}$
   - Distribuzioni dei valori estremi: Gumbel (code leggere), Fréchet/Pareto (code pesanti)

2. **Entropia** (§2, pp. 19-26)
   - [[Entropia di Shannon]] — $H(X)=-\sum p_i\log_2 p_i\in[0,\log_2 L]$
   - Informazione mutua $I(X;Y)=H(X)+H(Y)-H(X,Y)\geq 0$
   - Divergenza KL $D_{KL}(p\|q)=\sum p\log(p/q)\geq 0$

3. **Principio di massima entropia** (§3, pp. 27-32)
   - [[Principio di massima entropia]] — MaxEnt: $p(x)\propto e^{\sum\lambda_\alpha g_\alpha(x)}$
   - Distribuzione di Boltzmann-Gibbs, energia libera $F=-T\log Z$

4. **Sistemi di più variabili aleatorie** (§4, pp. 33-44)
   - [[Modello di Ising]] — Hamiltoniana 1D, distribuzione di Boltzmann
   - Matrice di trasferimento $Z=\text{Tr}(T^N)$, autovalori $\lambda_\pm$, rappresentazione spettrale
   - Magnetizzazione, correlazioni $C_{ij}=e^{-r/\xi}$, no transizione di fase in 1D

5. **Sistemi multidimensionali** (§5, pp. 45-59)
   - [[Modello di Curie-Weiss e Hopfield]] — Ising fully connected, equazione di campo medio $m=\tanh(\beta(Jm+h))$
   - Transizione di fase $T_c=J$, biforcazione, suscettività $\chi\sim 1/(T-T_c)$
   - Modello di Hopfield: regola di Hebb, memoria associativa, attrattori

## Concetti centrali

| Concetto | Argomento chiave |
|---|---|
| [[Funzione generatrice dei momenti]] | Cumulanti, TLC, grandi deviazioni |
| [[Teoria delle grandi deviazioni]] | Bound di Cramér, Gumbel, Fréchet |
| [[Entropia di Shannon]] | H, informazione mutua, divergenza KL |
| [[Principio di massima entropia]] | MaxEnt, distribuzione di Boltzmann-Gibbs |
| [[Modello di Ising]] | Matrice di trasferimento, correlazioni, 1D |
| [[Modello di Curie-Weiss e Hopfield]] | Campo medio, transizione di fase, Hopfield |

## Connessioni trasversali

- [[Recurrent Neural Network]] — il modello di Hopfield è una RNN con memoria associativa
- [[Multi-Layer Perceptron]] — confronto con architetture feed-forward
- [[Modelli Matematici per la Fisica I]] — prerequisito diretto (dinamica, ODE)
- [[Divergenza di Kullback-Leibler]] — $D_{KL}$ già vista in contesto ML

## Fonti del corso

- [[Dispense MMFII — Galletti]] — appunti completi (59 pp., A.A. 2024/2025)

## Stato

🟢 Completo
