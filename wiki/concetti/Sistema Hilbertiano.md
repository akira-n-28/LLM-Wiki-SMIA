---
tipo: concetto
titolo: Sistema Hilbertiano
tag: [fond-ai, logica, inferenza, derivabilità]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Sistema Hilbertiano

Un **sistema Hilbertiano** è un sistema di inferenza **sintattico**: permette di derivare formule (teoremi) a partire da assiomi applicando regole di inferenza, senza fare riferimento a modelli semantici.

## Sistema HAL (Hilbert Axiom Logic)

HAL è il sistema Hilbertiano per la **logica proposizionale**. Usa il linguaggio con soli connettivi $\lnot$ e $\to$.

**Assiomi** (schemi di formula):
1. $A \to (B \to A)$
2. $(A \to (B \to C)) \to ((A \to B) \to (A \to C))$
3. $(\lnot A \to \lnot B) \to (B \to A)$

**Regola di inferenza** — Modus Ponens:
$$\frac{A \quad A \to B}{B}$$

Non ci sono altri assiomi; tutti i connettivi rimanenti ($\land, \lor, \Leftrightarrow$) si riducono a $\lnot$ e $\to$.

## Derivabilità

**Definizione.** Sia $\Phi$ un insieme di formule, $A$ una formula. Una **derivazione** di $A$ da $\Phi$ è una sequenza finita non vuota $A_1, \ldots, A_n$ tale che $A_n = A$ e ogni $A_i$ è:
- un assioma, oppure
- una formula in $\Phi$, oppure
- il risultato di Modus Ponens applicato a due formule precedenti $A_j, A_k$ con $j, k < i$

Se esiste una derivazione, si scrive: $\Phi \vdash A$ (o $\Phi \vdash_{\text{HAL}} A$).

Se $\Phi = \emptyset$: $\vdash A$ significa che $A$ è un **teorema** di HAL.

## Proprietà di $\vdash$

1. $A \vdash A$ (riflessività)
2. Se $\Phi \vdash A$, allora $\Phi \cup \Gamma \vdash A$ (monotonicità)
3. Se $\Phi \vdash A$ e $A \vdash B$, allora $\Phi \vdash B$ (transitività)
4. Se $\vdash A$, allora $\Gamma \vdash A$ (uso di teoremi)
5. Se $\Phi \vdash A$ allora esiste $\Phi' \subseteq \Phi$ finito con $\Phi' \vdash A$ (compattezza)

## Teorema di deduzione (HAL)

**Teorema.** $\Phi \cup \{A\} \vdash B \iff \Phi \vdash A \to B$.

Equivalentemente: $A \vdash B \iff\ \vdash A \to B$ (cioè $B$ è derivabile da $A$ sse $A \to B$ è un teorema).

**Dimostrazione** ($\Leftarrow$): Se $\Phi \vdash A \to B$, estendo la derivazione con $A$ e applico MP per ottenere $B$ da $\Phi \cup \{A\}$.

**Dimostrazione** ($\Rightarrow$): Per induzione sulla derivazione $A_1, \ldots, A_n = B$ da $\Phi \cup \{A\}$. Ad ogni passo $k$ si dimostra che $\Phi \vdash A \to A_k$ sfruttando i 3 assiomi e il MP. $\square$

**Attenzione.** Il teorema di deduzione HAL (condizione di derivabilità) è diverso dal [[Conseguenza logica|teorema di deduzione semantico]] (che lega tautologie e conseguenza logica).

## Correttezza e completezza

Il sistema HAL è **corretto** e **completo** rispetto alla semantica proposizionale:

- **Correttezza**: $\vdash_{\text{HAL}} A \Rightarrow\ \models A$ (ogni teorema è tautologia)
- **Completezza**: $\models A \Rightarrow\ \vdash_{\text{HAL}} A$ (ogni tautologia è dimostrabile)

La correttezza si prova verificando che i 3 assiomi sono tautologie e che MP preserva la verità.

## Sistema Hilbertiano per la logica del primo ordine

Estende HAL con linguaggio $\to, \lnot, \forall$. Si aggiungono:

**Assiomi addizionali:**
4. $\forall x A \to A[x/t]$ se $t$ è sostituibile a $x$ in $A$
5. $\forall x(A \to B) \to ((\forall x A) \to (\forall x B))$ se $A$ non ha occorrenze libere di $x$

**Regola aggiuntiva** — Generalizzazione:
$$\frac{A}{\forall x A}$$

Il teorema di deduzione si estende: $\Phi \vdash_{\text{HAL}} B \iff \Phi \vdash_{\text{HAL}} A \to B$.

Il sistema rimane corretto e completo per la [[Logica del primo ordine]].

## Consistenza di una KB

Una base di conoscenza $\Phi$ è **consistente** (semanticamente) se esiste almeno un modello che la soddisfa; (sintatticamente) se non è derivabile una contraddizione.

Un sistema corretto garantisce che la consistenza sintattica implica quella semantica.

## Ragionamento ritrattabile

L'aggiunta di nuove formule a $\Phi$ può portare alla **ritrattazione** di formule precedentemente derivate — il sistema è **non monotonico** in senso applicativo (anche se la relazione $\vdash$ è tecnicamente monotona, la KB può diventare inconsistente).

## Confronto tra sistemi

| Sistema | Approccio | Linguaggio di lavoro |
|---|---|---|
| HAL | Derivazione sintattica | Formule LP con $\lnot, \to$ |
| [[Alberi di Beth]] | Refutazione semantica | Formule LP generali |
| [[Risoluzione (RES)]] | Refutazione su clausole | CNF |

## Vantaggi e svantaggi

**Vantaggi:** il ragionamento è completamente sintattico, non richiede modelli.
**Svantaggi:** trovare la derivazione giusta è difficile; praticabile per piccole KB o con euristica.

## Collegament

- Prerequisito di: [[Risoluzione (RES)]] (CNF e clausole), [[Clausole di Horn]]
- Si fonda su: [[Conseguenza logica]], [[Logica proposizionale]]
- Discusso in: [[Fondamenti di Intelligenza Artificiale]]

## Fonti

- [[Dispense FondAI — Galletti]] §6, §7.3
