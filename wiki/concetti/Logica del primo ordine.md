---
tipo: concetto
titolo: Logica del primo ordine
tag: [fond-ai, logica, inferenza, predicati, quantificatori]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Logica del primo ordine

La **logica del primo ordine** (LPO) estende la [[Logica proposizionale]] con **predicati**, **termini** (costanti, variabili, funzioni) e **quantificatori** $\forall, \exists$. Permette di esprimere relazioni tra oggetti, non solo fatti atomici.

## Sintassi

### Simboli

**Simboli logici:**
- Variabili (insieme numerabile)
- Connettivi: $\lnot, \land, \lor, \to, \leftrightarrow$
- Costanti proposizionali: $\bot, \top$
- Quantificatori: $\forall$ ("per ogni"), $\exists$ ("esiste")

**Simboli non logici** (specifici del dominio):
- **Simboli di predicato** di arità $n$ (includono $=$)
- **Costanti individuali**
- **Simboli funzionali** (funtori) di arità $n$

### Termini

I **termini** sono le unità sintattiche di base:
1. Ogni variabile è un termine
2. Ogni costante è un termine
3. Se $f^n$ è un funtore di arità $n$ e $t_1, \ldots, t_n$ sono termini, allora $f^n(t_1, \ldots, t_n)$ è un termine

Un termine **chiuso** non contiene variabili.

### Formule ben formate

1. **Formule atomiche**: $P^n(t_1, \ldots, t_n)$, $\bot$, $\top$, $t_1 = t_2$
2. Se $A$ è formula: $\lnot A$ è formula
3. Se $A, B$ sono formule: $A \land B$, $A \lor B$, $A \to B$, $A \leftrightarrow B$ sono formule
4. Se $A$ è formula e $x$ variabile: $\forall x A$ e $\exists x A$ sono formule

### Variabili libere e vincolate

Un'occorrenza di $x$ in $A$ è **vincolata** se cade dentro $\forall x A'$ o $\exists x A'$; altrimenti è **libera**.

$$\text{freevars}(\forall x B) = \text{freevars}(B) \setminus \{x\}$$

Una formula **chiusa** non ha occorrenze libere di variabili.

### Sostituzione

La sostituzione $E[t/x]$ rimpiazza ogni **occorrenza libera** di $x$ in $E$ con il termine $t$.

**Sostituzione simultanea**: $\theta = [t_1/x_1, \ldots, t_n/x_n]$ — si applicano tutte le sostituzioni nello stesso passaggio (non equivalente a sostituzioni sequenziali).

**Composizione di sostituzioni**: $E(\theta \circ \sigma) = (E\theta)\sigma$.

## Semantica

### Struttura (realizzazione)

Una **struttura** $\mathcal{M}$ per un linguaggio $L$ è:
1. Un **dominio** $M \neq \emptyset$ (universo del discorso)
2. Interpretazione delle costanti: $c^\mathcal{M} \in M$ per ogni costante $c$
3. Interpretazione dei predicati: $P^\mathcal{M} \subseteq M^n$ per ogni predicato $P$ di arità $n$
4. Interpretazione dei funtori: $f^\mathcal{M}: M^n \to M$

Un'**assegnazione** $s$ mappa variabili a elementi del dominio $M$.

### Soddisfacibilità

Si scrive $(\mathcal{M}, s) \models A$ (la formula $A$ è vera in $\mathcal{M}$ secondo $s$):

$$(\mathcal{M}, s) \models P(t_1, \ldots, t_n) \iff \bar{s}(t_1), \ldots, \bar{s}(t_n) \in P^\mathcal{M}$$
$$(\mathcal{M}, s) \models \forall x A \iff \text{per ogni } d \in M,\ (\mathcal{M}, s[d/x]) \models A$$
$$(\mathcal{M}, s) \models \exists x A \iff \text{esiste } d \in M \text{ tale che } (\mathcal{M}, s[d/x]) \models A$$

(Le condizioni per i connettivi proposizionali sono le stesse di [[Logica proposizionale]].)

Una formula $A$ è **vera** in $\mathcal{M}$ (scriviamo $\mathcal{M} \models A$) se vale per ogni assegnazione $s$.

### Tautologie, soddisfacibilità, conseguenza logica

- $A$ è **valida** (tautologia) se è vera in ogni struttura
- $A$ è **contraddittoria** se è falsa in ogni struttura
- $A$ è **soddisfacibile** se esiste una struttura e assegnazione in cui è vera
- $\Phi \models A$: $A$ è conseguenza logica di $\Phi$ se ogni struttura/assegnazione che soddisfa $\Phi$ soddisfa $A$

**Proprietà fondamentale:**
$$\Phi \models A \iff \Phi \cup \{\lnot A\} \text{ è insoddisfacibile}$$

## Decidibilità

| Logica | Decidibilità |
|---|---|
| Logica proposizionale | Decidibile ($O(2^n)$) |
| Logica del primo ordine | **Indecidibile** (riconducibile al problema della fermata) |

Il sistema è **semidecidibile**: se $S \models A$, il processo termina; se $S \not\models A$, potrebbe non terminare.

**Distinguere completezza e decidibilità:**
- **Completezza**: ogni formula valida ammette una dimostrazione
- **Decidibilità**: determinare se una formula arbitraria è valida è risolvibile in tempo finito

Casi decidibili in LPO: calcolo monadico (predicati unari), formule puramente universali/esistenziali.

## Unificazione

L'**unificazione** è il meccanismo che permette di applicare regole generali a casi specifici.

**Definizione.** Un **unificatore** di $\{E_1, \ldots, E_k\}$ è una sostituzione $\theta$ tale che $E_1\theta = E_2\theta = \cdots = E_k\theta$.

**Unificatore più generale (mgu)**: $\theta$ è mgu se per ogni altro unificatore $\sigma$ esiste $\lambda$ tale che $\theta = \sigma \circ \lambda$. L'mgu è il più "generale" (meno impegna le variabili).

### Algoritmo di Robinson

```
A₀ ← A, B₀ ← B, σ₀ ← ∅
loop:
  if Aᵢ = Bᵢ: return σᵢ  (già unificati)
  seleziona il disagreement set {e, e'} tra Aᵢ e Bᵢ
  if esiste xᵢ ∈ {e, e'} variabile e l'altro eᵢ non contiene xᵢ:
    σᵢ₊₁ ← σᵢ ∘ {eᵢ/xᵢ}
    Aᵢ₊₁ ← Aᵢ{eᵢ/xᵢ}, Bᵢ₊₁ ← Bᵢ{eᵢ/xᵢ}
  else: return fail
```

**Disagreement set**: le due sottoespressioni che iniziano alla posizione più a sinistra dove $A$ e $B$ differiscono.

**Esempio**: $A = p(x, f(c), x)$, $B = p(x, g(y,a), z)$ → disagreement set: $\{f(c), g(y,a)\}$ → impossibile unificare (clash di simboli di funzione) → **fail**.

**Complessità**: nel caso peggiore esponenziale, ma esistono implementazioni polinomiali.

## Forma a clausole (per risoluzione)

Per applicare la [[Risoluzione (RES)]] alla LPO si converte in **forma a clausole**:

1. **Forma prenessa**: $Q_1 x_1 \cdots Q_n x_n (A)$ — tutti i quantificatori portati davanti, $A$ senza quantificatori

2. **Skolemizzazione** (forma normale di Skolem): eliminare i quantificatori esistenziali:
   $$\forall x_1 \cdots \forall x_n \exists y\ A \;\Rightarrow\; \forall x_1 \cdots \forall x_n A[f(x_1, \ldots, x_n)/y]$$
   dove $f$ è un nuovo **simbolo di Skolem** (funzione che dipende dalle variabili universali precedenti).
   La skolemizzazione **preserva la soddisfacibilità** (non l'equivalenza logica).

3. **Eliminazione dei quantificatori universali** (implicita, si lavora su variabili libere)

4. **Conversione in CNF** della matrice

5. **Separazione in clausole**

**Teorema**: $A$ è insoddisfacibile $\iff$ la sua forma a clausole è insoddisfacibile.

## Risoluzione con unificazione

La **regola di risoluzione LPO**: date clausole $C_1 \cup \{P\}$ e $C_2 \cup \{\lnot Q\}$ con $\theta$ mgu di $P$ e $Q$:

$$\frac{C_1 \cup \{P\} \quad C_2 \cup \{\lnot Q\}}{C_1\theta \cup C_2\theta}$$

## Teorie del primo ordine

Una **teoria del primo ordine** è composta da:
- Linguaggio del primo ordine
- Assiomi logici + regole di inferenza + **assiomi propri** (specifici del dominio)

**Teorie con uguaglianza**: includono assiomi di riflessività $\forall x (x = x)$ e sostituzione $\forall x \forall y (x = y \to (A \to \hat{A}))$.

## Confronto con logica proposizionale

| Aspetto | LP | LPO |
|---|---|---|
| Enunciati atomici | Variabili $A_i$ | Predicati $P(t_1, \ldots, t_n)$ |
| Relazioni tra oggetti | No | Sì |
| Quantificatori | No | $\forall, \exists$ |
| Decidibilità | Sì | No |
| Complessità verifica | $O(2^n)$ | Semidecidibile |

## Collegament

- Estende: [[Logica proposizionale]]
- Usa: [[Conseguenza logica]], [[Risoluzione (RES)]], [[Sistema Hilbertiano]]
- Permette: [[Clausole di Horn]] con unificazione
- Discusso in: [[Fondamenti di Intelligenza Artificiale]]

## Fonti

- [[Dispense FondAI — Galletti]] §7
