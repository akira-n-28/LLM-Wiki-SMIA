---
tipo: concetto
titolo: Conseguenza logica
tag: [fond-ai, logica, inferenza]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Conseguenza logica

**Definizione.** Date due formule proposizionali $F_1$ e $F_2$, si dice che $F_2$ è **conseguenza logica** di $F_1$ se $F_2$ è vera in ogni modello di $F_1$:

$$F_1 \models F_2 \iff \mathcal{M}(F_1) \subseteq \mathcal{M}(F_2)$$

dove $\mathcal{M}(F)$ è l'insieme dei modelli di $F$. In altri termini, $F_1$ è "più forte" di $F_2$ (esclude più modelli).

**Estensione a insiemi.** Dato un insieme di formule $\Phi$ e una formula $A$: $\Phi \models A$ se ogni modello che soddisfa tutte le formule di $\Phi$ soddisfa anche $A$.

## Inferenza corretta

Un'**inferenza** è **corretta** se e solo se la formula conclusiva è conseguenza logica delle premesse. Equivalentemente, ogni modello delle premesse è modello della conclusione.

**Esempio** (sillogismo corretto):
$$A \to B,\; B \to C \;\models\; A \to C$$

## Teorema di deduzione

**Teorema.** Siano $A_1, \ldots, A_n$ e $A$ formule. Allora:

$$A_1 \land \cdots \land A_n \models A \iff (A_1 \land \cdots \land A_n) \to A \text{ è tautologia}$$

**Corollario.** Per due formule $\alpha, \beta$:

$$\alpha \models \beta \iff \alpha \to \beta \text{ è tautologia}$$

**Dimostrazione** ($\Rightarrow$): se $\exists M$ tale che $M \models (A_1 \land \cdots \land A_n)$ ma $M \not\models A$, questo contraddirebbe $A_1 \land \cdots \land A_n \models A$. ($\Leftarrow$): se la tautologia vale, allora ogni modello che soddisfa le premesse soddisfa $A$ per definizione di implicazione. $\square$

## Model checking

**Metodo diretto** per verificare $\alpha \models \beta$: costruire la tavola di verità di $\alpha \to \beta$ e verificare se è tautologia.

- **Corretto e completo**: implementa la definizione semantica
- **Complessità**: $O(2^n)$ dove $n$ è il numero di variabili proposizionali — impraticabile per KB grandi

## Sistema di inferenza

**Definizione.** Un **sistema di inferenza** è composto da:
- Un insieme di **assiomi** (schemi di formule dati per buoni)
- Un insieme di **regole di inferenza** $R = \{R_1, \ldots, R_k\}$ che derivano nuove formule

**Correttezza**: ogni formula derivata è conseguenza logica della KB.
**Completezza**: ogni conseguenza logica della KB è derivabile.

## Metodi alternativi per verificare $\alpha \models \beta$

1. Tavola di verità per $\alpha \to \beta$: verifica che sia tautologia
2. Alberi di Beth: cfr. [[Alberi di Beth]]
3. Derivazione tramite sistema Hilbertiano: cfr. [[Sistema Hilbertiano]]
4. Risoluzione: cfr. [[Risoluzione (RES)]]

## Esempio: cavalieri e furfanti

$A$ afferma "Io sono un furfante oppure $B$ è cavaliere". Formalizzazione:
$$A \to (\lnot A \lor B), \quad \lnot A \to \lnot(\lnot A \lor B)$$

Model checking: l'unico modello soddisfacente ha $A = 1, B = 1$. Entrambi sono cavalieri.

## Conseguenza logica nella logica del primo ordine

La definizione si estende a [[Logica del primo ordine]]: $\Phi \models A$ se per ogni struttura $M$ e assegnazione $s$, $(M, s) \models C$ per ogni $C \in \Phi$ implica $(M, s) \models A$.

## Equivalenza logica

$\alpha \equiv \beta$ (logicamente equivalenti) $\iff$ $\alpha \models \beta$ e $\beta \models \alpha$ $\iff$ $\alpha \Leftrightarrow \beta$ è tautologia.

## Ragionamento ritrattabile

Si parla di **ragionamento ritrattabile** quando l'aggiunta di nuove informazioni alla KB può invalidare conclusioni precedentemente derivate. Una KB è **consistente** se esiste almeno un modello che la soddisfa.

## Relazione con derivabilità

La **derivabilità** ($\Phi \vdash A$) è la nozione sintattica corrispondente alla conseguenza logica (nozione semantica). Un sistema di inferenza corretto e completo garantisce $\Phi \models A \iff \Phi \vdash A$.

## Collegamenti

- Prerequisito di: [[Alberi di Beth]], [[Sistema Hilbertiano]], [[Risoluzione (RES)]]
- Si fonda su: [[Logica proposizionale]]
- Estesa in: [[Logica del primo ordine]]
- Discusso in: [[Fondamenti di Intelligenza Artificiale]]

## Fonti

- [[Dispense FondAI — Galletti]] §4
