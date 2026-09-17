---
tipo: concetto
titolo: Logica proposizionale
tag: [fond-ai, logica, inferenza]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Logica proposizionale

La logica proposizionale è il sistema formale base per rappresentare conoscenza dichiarativa (fatti e relazioni tra oggetti) e ragionarci sopra.

## Sintassi

**Simboli del linguaggio:**

- Variabili proposizionali: $A_1, A_2, \ldots, A_n$
- Costanti: $\bot$ (falso), $\top$ (vero)
- Connettivi logici: $\land$ (AND), $\lor$ (OR), $\lnot$ (NOT), $\Rightarrow$ (implicazione), $\Leftrightarrow$ (bicondizionale)
- Simboli ausiliari: parentesi

**Formule ben formate** (induzione):
1. Ogni variabile proposizionale è una formula
2. $\top$ e $\bot$ sono formule
3. Se $\alpha$ è formula, $\lnot \alpha$ è formula
4. Se $\alpha, \beta$ sono formule, lo sono anche $\alpha \land \beta$, $\alpha \lor \beta$, $\alpha \Rightarrow \beta$, $\alpha \Leftrightarrow \beta$
5. Nient'altro è formula

**Precedenza dei connettivi** (da più a meno legante): $\lnot, \land, \lor, \Rightarrow, \Leftrightarrow$.

**Osservazione.** Si può esprimere tutto con soli $\lnot$ e $\Rightarrow$:
$$A \land B \equiv \lnot(A \Rightarrow \lnot B), \quad A \lor B \equiv \lnot A \Rightarrow B$$

## Semantica

**Tre principi:**
- **Determinatezza**: ogni formula si trova in uno e uno solo stato di verità
- **Bivalenza**: ogni formula è vera o falsa (no terzo valore)
- **Estensione**: il valore di verità di una formula dipende solo dai valori degli enunciati atomici e dai connettivi

**Tavole di verità dei connettivi principali:**

| $A$ | $B$ | $\lnot A$ | $A \land B$ | $A \lor B$ | $A \Rightarrow B$ | $A \Leftrightarrow B$ |
|---|---|---|---|---|---|---|
| 1 | 1 | 0 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 | 1 | 1 | 0 |
| 0 | 0 | 1 | 0 | 0 | 1 | 1 |

L'implicazione $A \Rightarrow B$ è falsa solo quando $A$ è vera e $B$ è falsa.

## Modelli

**Definizione.** Un **modello** $M$ è un'assegnazione di valori booleani agli enunciati atomici:

$$M: P \to \{0, 1\}$$

Si scrive $M \models \alpha$ se $\alpha$ è vera in $M$. La relazione $\models$ si definisce per induzione:

$$M \models p \iff M(p) = 1$$
$$M \models \lnot \alpha \iff M \not\models \alpha$$
$$M \models \alpha \land \beta \iff M \models \alpha \text{ e } M \models \beta$$
$$M \models \alpha \lor \beta \iff M \models \alpha \text{ o } M \models \beta$$
$$M \models \alpha \Rightarrow \beta \iff M \not\models \alpha \text{ o } M \models \beta$$

Un **contromodello** di $A$ è un $M$ tale che $M \not\models A$.

## Soddisfacibilità e tautologie

- $A$ è **soddisfacibile** se esiste un modello $M$ tale che $M \models A$
- $A$ è una **tautologia** (formula valida) se è vera in ogni modello
- $A$ è una **contraddizione** se è falsa in ogni modello

**Esempi di tautologie:**
- Principio di non-contraddizione: $\lnot(A \land \lnot A)$
- Principio del terzo escluso: $A \lor \lnot A$
- Legge di De Morgan I: $\lnot(A \lor B) \Leftrightarrow (\lnot A \land \lnot B)$
- Legge di De Morgan II: $\lnot(A \land B) \Leftrightarrow (\lnot A \lor \lnot B)$
- Contrapposizione: $(A \Rightarrow B) \Leftrightarrow (\lnot B \Rightarrow \lnot A)$

## Equivalenza logica

Due formule $\alpha, \beta$ sono **logicamente equivalenti** ($\alpha \equiv \beta$) se $\alpha \models \beta$ e $\beta \models \alpha$, equivalentemente se $\alpha \Leftrightarrow \beta$ è tautologia.

## Esempio: Mondo del Wumpus

Con variabili proposizionali $P_{xy}$ (pozzo in $[x,y]$), $B_{xy}$ (brezza in $[x,y]$) ecc., si può codificare conoscenza del tipo:

$$R_2: B_{11} \Leftrightarrow (P_{12} \lor P_{21})$$

e dedurre fatti (es. $\lnot P_{12}$) per model checking.

## Differenza con logica del primo ordine

In LP gli enunciati atomici sono singole variabili $A_i$ senza struttura interna. La [[Logica del primo ordine]] introduce predicati $P(t_1, \ldots, t_n)$ su termini, aumentando enormemente la potenza espressiva.

## Limiti della logica proposizionale

- Non può esprimere relazioni tra oggetti
- La verifica di conseguenza logica (model checking) ha complessità $O(2^n)$ nel numero di variabili

## Metodi di inferenza

1. **Model checking** (tavole di verità): esegue $O(2^n)$ — cfr. [[Conseguenza logica]]
2. **Alberi di Beth**: refutazione automatica — cfr. [[Alberi di Beth]]
3. **Sistema Hilbertiano (HAL)**: derivazione sintattica — cfr. [[Sistema Hilbertiano]]
4. **Risoluzione (RES)**: su formule in CNF — cfr. [[Risoluzione (RES)]]

## Forma normale congiuntiva (CNF)

Ogni formula è logicamente equivalente a una **congiunzione di clausole** (CNF). Le clausole sono disgiunzioni di letterali; i letterali sono variabili proposizionali o loro negazioni.

Conversione in CNF:
1. Eliminare $\Leftrightarrow$: $A \Leftrightarrow B \equiv (A \Rightarrow B) \land (B \Rightarrow A)$
2. Eliminare $\Rightarrow$: $A \Rightarrow B \equiv \lnot A \lor B$
3. Portare $\lnot$ verso l'interno (De Morgan, doppia negazione)
4. Distribuire $\lor$ su $\land$

## Collegamenti

- Prerequisito di: [[Conseguenza logica]], [[Alberi di Beth]], [[Sistema Hilbertiano]], [[Risoluzione (RES)]]
- Estesa da: [[Logica del primo ordine]]
- Discusso in: [[Fondamenti di Intelligenza Artificiale]]

## Fonti

- [[Dispense FondAI — Galletti]] §3
