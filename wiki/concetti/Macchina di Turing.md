---
tipo: concetto
titolo: Macchina di Turing
tag: [algoritmi, complessità, teoria-della-computazione]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-05
---

# Macchina di Turing

## Definizione formale

Una **macchina di Turing** (MT) è una 8-tupla:
$$M = (Q,\, \Gamma,\, \Sigma,\, \delta,\, \vdash,\, \sqcup,\, s,\, a,\, r)$$

- $Q$: insieme finito di stati; $s,a,r \in Q$ (start, accept, reject)
- $\Gamma$: alfabeto del nastro; $\Sigma \subsetneq \Gamma$: alfabeto di input
- $\delta: Q \times \Gamma \to Q \times \Gamma \times \{L, -, R\}$: funzione di transizione
- $\vdash, \sqcup \in \Gamma \setminus \Sigma$: marcatore di inizio e cella vuota

La MT ha un nastro infinito, una testina lettura/scrittura e un controllo finito. Ogni processo calcolabile da un computer è simulabile da una MT (**Tesi di Church-Turing**).

## Decidibilità

Un linguaggio $L \subseteq \Sigma^*$ è **decidibile** se esiste una MT $M$ tale che $\forall x \in \Sigma^*$:
- $x \in L \Rightarrow M(x)$ accetta
- $x \notin L \Rightarrow M(x)$ rifiuta

## Problema dell'Halting (HP)

$$\mathrm{HP} = \{ M\#x \mid M(x) \text{ si ferma} \}$$

**Teorema (Turing, 1936):** HP non è decidibile.

*Dimostrazione per diagonalizzazione:* si suppone che esista $\hat{H}(i,j)$ che decide $H(i) \equiv \hat{H}(i,i)$. Si costruisce $D(x) = \overline{H(x)}$ (la MT che fa l'opposto). Se $D = M_k$: $M_k(k)$ si ferma $\Leftrightarrow D(k) = \text{No}$ $\Leftrightarrow M_k(k)$ non si ferma — contraddizione.

## Riduzioni e indecidibilità

Se $A \leq_T B$ e $A$ è indecidibile, allora $B$ è indecidibile.

**Catena:** $\mathrm{HP} \leq_T A \leq_T F \leq_T E \leq_T \mathrm{EQ}$

dove:
- $A = \{M\#x \mid M(x) \text{ accetta}\}$
- $F = \{M \mid M \text{ accetta almeno un input}\}$
- $E = \{M \mid M \text{ non accetta nessun input}\}$ (complemento di $F$)
- $\mathrm{EQ} = \{M_1\#M_2 \mid M_1 \equiv M_2\}$

Tutti questi linguaggi sono indecidibili.

## MT non deterministica

La MT non deterministica accetta se **esiste** un ramo di computazione che si ferma in stato di accettazione.

**Teorema:** i linguaggi decidibili da TM deterministiche coincidono con quelli decidibili da TM non deterministiche.

## Connessioni

- Complessità: [[NP-completezza]], [[Complessità computazionale]]
- Logica: [[Logica del primo ordine]] (decidibilità, semi-decidibilità)
- Contesto storico: Alan Turing, David Hilbert (Entscheidungsproblem)
- Discusso in: [[Algoritmi e Complessità]]

## Fonti

- [[Dispense Algoritmi — Galletti]] (§6-7, pp. 40-44)
