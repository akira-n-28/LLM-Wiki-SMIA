---
tipo: concetto
titolo: NP-completezza
tag: [algoritmi, complessità, matematica]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-05
---

# NP-completezza

## Classi di complessità

| Classe | Definizione |
|---|---|
| **P** | Problemi decisionali risolvibili in tempo polinomiale deterministico |
| **NP** | Problemi decisionali in cui una soluzione "sì" è **verificabile** in tempo polinomiale |
| **NP-completo** | $X \in$ NP e $\forall Y \in$ NP: $Y \leq X$ (riduzione polinomiale) |

**Relazione:** $P \subseteq NP$. Aperto se $P = NP$.

## Riduzioni polinomiali

$A \leq B$ ("$A$ si riduce a $B$"): esiste $f$ calcolabile in tempo polinomiale tale che $x \in A \Leftrightarrow f(x) \in B$.

**Proprietà:** se $A \leq B$ e $B \in P$, allora $A \in P$. Se $A \leq B$ e $A \notin P$, allora $B \notin P$.

## Teorema di Cook-Levin

**SAT è NP-completo.** Dato $F(x_1,\ldots,x_n) = C_1 \wedge \cdots \wedge C_m$ (CNF), esiste $\tau: X \to \{T,F\}$ che soddisfa $F$?

Ogni $Y \in$ NP si riduce a SAT in tempo polinomiale.

## Catena di riduzioni

$$\text{SAT} \leq \text{3-SAT} \leq \text{3-Coloring} \qquad \text{SAT} \leq \text{Clique} \leq \text{IS} \leq \text{Vertex Cover} \leq \text{SubsetSum} \leq \text{Partition} \leq \text{Knapsack}$$

| Problema | Descrizione | Riduzione da |
|---|---|---|
| **3-SAT** | SAT con clausole di lunghezza ≤ 3 | SAT (variabili ausiliarie) |
| **Clique** | Esiste clique di dimensione $k$? | SAT (letterali = nodi, archi tra compatibili) |
| **Independent Set** | Esiste IS di dimensione $k$? | Clique (grafo complemento) |
| **Vertex Cover** | Esiste cover di dimensione $k$? | IS ($I$ IS $\Leftrightarrow$ $V \setminus I$ cover, $k' = n-k$) |
| **SubsetSum** | Esiste $A \subseteq V$ con $\sum A = t$? | Exact Cover (codifica in base $m+1$) |
| **Partition** | Esiste bipartizione di ugual somma? | SubsetSum (aggiunta di elementi $N\pm t$) |
| **Knapsack** | Sottoinsieme con peso $\leq W$, valore $\geq B$? | Partition ($w_i = b_i = x_i$, $W=B=\frac{1}{2}\sum x_i$) |
| **3-Coloring** | Esiste colorazione con 3 colori? | SAT (gadget per clausole) |

## Significato pratico

Dimostrare che $X$ è NP-completo implica che un algoritmo polinomiale per $X$ risolverebbe **tutti** i problemi in NP. Nessuno ci è riuscito: per questi problemi si usano euristiche, approssimazioni, o si limita la dimensione dell'input.

## Connessioni

- Fondamenta: [[Complessità computazionale]], [[Macchina di Turing]]
- Algoritmi esatti: [[Programmazione dinamica]] (SubsetSum/Knapsack in tempo $O(nW)$ — pseudopolinomiale)
- Riduzione classica in [[Logica del primo ordine]] (SAT, clausole di Horn)
- Discusso in: [[Algoritmi e Complessità]]

## Fonti

- [[Dispense Algoritmi — Galletti]] (§5, pp. 29-39)
