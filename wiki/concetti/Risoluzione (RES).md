---
tipo: concetto
titolo: Risoluzione (RES)
tag: [fond-ai, logica, inferenza, clausole, cnf]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Risoluzione (RES)

La **risoluzione** è un sistema di inferenza per la logica proposizionale (e del primo ordine) basato su un'unica regola di inferenza applicata a formule in **Forma Normale Congiuntiva (CNF)**. Non ha assiomi.

## Terminologia

- **Letterale**: variabile proposizionale $p$ o sua negazione $\lnot p$
- **Clausola**: disgiunzione di letterali $l_1 \lor \cdots \lor l_n$, rappresentata come insieme $\{l_1, \ldots, l_n\}$
- **Clausola unitaria**: clausola con un solo letterale
- **Clausola vuota** $\bot$ ($\square$): la clausola senza letterali — rappresenta la contraddizione (falso)
- **CNF**: congiunzione di clausole

## Regola di risoluzione

**Risoluzione binaria**: date due clausole $C_1 = A \lor l$ e $C_2 = B \lor \lnot l$, il loro **risolvente** è:

$$C_1 \text{ res } C_2 = A \lor B$$

Si risolve sulla coppia di letterali complementari $l$ e $\lnot l$, eliminandoli.

**Correttezza della regola.** Se $C_1$ e $C_2$ sono vere in un'interpretazione $I$:
- Se $l$ è vero in $I$: $\lnot l$ è falso, quindi almeno un letterale di $B$ è vero → $A \lor B$ è vera
- Se $l$ è falso in $I$: almeno un letterale di $A$ è vero → $A \lor B$ è vera

Ogni applicazione preserva la verità. $\square$

## Derivabilità per risoluzione

Sia $\Phi$ un insieme di clausole. Una **derivazione** di $A$ da $\Phi$ tramite risoluzione è una sequenza $C_1, \ldots, C_n$ tale che $C_n = A$ e ogni $C_i$ è:
- una clausola di $\Phi$, oppure
- il risolvente di due clausole precedenti $C_j, C_k$ con $j, k < i$

Si scrive $\Phi \vdash_{\text{RES}} A$. Se $\Phi = \emptyset$, $\vdash_{\text{RES}} A$ significa che $A$ è un teorema RES.

**Esempio.** Con $\Phi = \{\lnot p \lor q,\ p \lor r,\ \lnot q \lor s\}$:

$$\{q, r\} \text{ (risolvente di 1 e 2 su } p) \quad \to \quad \{r, s\} \text{ (risolvente con 3 su } q)$$

Quindi $\Phi \vdash_{\text{RES}} r \lor s$.

## Refutazione per risoluzione

La risoluzione è potente soprattutto come **metodo di refutazione**:

$$\Phi \models A \iff \Phi \cup \{\lnot A\} \text{ è insoddisfacibile} \iff \Phi \cup \{\lnot A\} \vdash_{\text{RES}} \bot$$

**Procedura di dimostrazione:**
1. Convertire tutte le formule di $\Phi \cup \{\lnot A\}$ in CNF
2. Applicare ripetutamente la regola di risoluzione
3. Se si deriva $\bot$ → $\Phi \cup \{\lnot A\}$ è insoddisfacibile → $\Phi \models A$ ✓
4. Se non si aggiungono nuove clausole senza derivare $\bot$ → $\Phi \not\models A$

**Esempio di refutazione.** Dimostrare $\{p \to q, q \to r\} \models p \to r$:

$$\Phi' = \{\{\lnot p, q\},\ \{\lnot q, r\},\ \{p\},\ \{\lnot r\}\}$$

1. $\{q\}$ (da $\{\lnot p, q\}$ e $\{p\}$)
2. $\{r\}$ (da $\{\lnot q, r\}$ e $\{q\}$)
3. $\bot$ (da $\{r\}$ e $\{\lnot r\}$) ✓

## Completezza della risoluzione

**Teorema** (completezza per refutazione). Se $\Phi \models A$, allora $\Phi \cup \{\lnot A\} \vdash_{\text{RES}} \bot$.

**Equivalentemente**: $\Phi$ è insoddisfacibile $\iff$ $\Phi \vdash_{\text{RES}} \bot$.

**Dimostrazione** (per assurdo): se $\Phi \not\vdash_{\text{RES}} \bot$, allora $\bot \notin \text{RC}(\Phi)$ (chiusura per risoluzione). Si costruisce esplicitamente un modello di $\Phi$ assegnando valori alle variabili in ordine $P_1, \ldots, P_k$: $P_i$ riceve valore 0 (falso) se esiste una clausola nella chiusura con $\lnot P_i$ e tutti gli altri letterali già falsificati; altrimenti 1. Si dimostra per assurdo che questa assegnazione soddisfa $\Phi$. $\square$

## Fattorizzazione

Quando si applica la risoluzione a $p \lor q$ e $p \lor \lnot q$, il risolvente è $p \lor p$. La **fattorizzazione** elimina letterali duplicati:

$$\frac{C \lor l \lor l}{C \lor l}$$

Adottando la convenzione che le clausole sono **insiemi** di letterali, la fattorizzazione è automatica. Con fattorizzazione, la risoluzione è **completa per refutazione**.

## Algoritmo PL-RISOLUZIONE

```
PL-RISOLUZIONE(KB, α) → true / false
  clausole ← CNF(KB ∧ ¬α)
  nuove ← ∅
  loop:
    for each coppia (Ci, Cj) in clausole:
      risolventi ← PL-RISOLVI(Ci, Cj)
      if ⊥ ∈ risolventi: return true
      nuove ← nuove ∪ risolventi
    if nuove ⊆ clausole: return false
    clausole ← clausole ∪ nuove
```

Versione più efficiente: **risoluzione lineare** — si sceglie una clausola iniziale $C_0$ e si risolve sempre con essa o con clausole derivate, evitando ridondanze.

## Proprietà del sistema RES

| Proprietà | Enunciato |
|---|---|
| Correttezza | $\Phi \vdash_{\text{RES}} A \Rightarrow \Phi \models A$ |
| Completezza (per refutazione) | $\Phi \models A \Rightarrow \Phi \cup \{\lnot A\} \vdash_{\text{RES}} \bot$ |

## Risoluzione nella logica del primo ordine

Nel caso del primo ordine, la regola di risoluzione usa l'**unificazione**: date clausole $C_1 \cup \{P\}$ e $C_2 \cup \{\lnot Q\}$, se $\theta$ è l'mgu di $P$ e $Q$:

$$\frac{C_1 \cup \{P\} \quad C_2 \cup \{\lnot Q\}}{C_1\theta \cup C_2\theta}$$

Per applicare la risoluzione al primo ordine si passa prima alla **forma a clausole** tramite skolemizzazione — cfr. [[Logica del primo ordine]].

## Relazione con altri sistemi

- [[Conseguenza logica]]: la risoluzione implementa la verifica di $\models$
- [[Sistema Hilbertiano]]: sistema alternativo sintattico (HAL)
- [[Alberi di Beth]]: sistema alternativo semantico
- [[Clausole di Horn]]: caso speciale con algoritmi più efficienti

## Discusso in: [[Fondamenti di Intelligenza Artificiale]]

## Fonti

- [[Dispense FondAI — Galletti]] §6.2–6.4, §7 (risoluzione LPO)
