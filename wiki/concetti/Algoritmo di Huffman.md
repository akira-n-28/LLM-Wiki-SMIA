---
tipo: concetto
titolo: Algoritmo di Huffman
tag: [algoritmi, compressione, greedy, alberi]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-05
---

# Algoritmo di Huffman

## Prefix-Code

Un **prefix-code** per un alfabeto $S$ è una funzione $\gamma: S \to \{0,1\}^*$ tale che nessuna codifica è prefisso di un'altra. Equivalente a un albero binario con le lettere sulle foglie.

**ABL** (Average Bit Length): costo medio in bit per simbolo:
$$\mathrm{ABL}(\gamma) = \sum_{x \in S} f_x \cdot |\gamma(x)| = \mathrm{ABL}(T) = \sum_{x \in S} f_x \cdot \mathrm{Depth}_T(x)$$

## Proprietà dell'albero ottimo

Siano $T^*$ un albero ottimo e $y, z$ due lettere di **minima frequenza**:

- **Lemma (albero pieno):** $T^*$ è pieno (ogni nodo interno ha esattamente 2 figli).
- **Lemma (profondità e frequenza):** se $\mathrm{Depth}(u) < \mathrm{Depth}(v)$ allora $f_u \geq f_v$.
- **Lemma (sorelle di minima freq.):** esiste un ottimo in cui $y$ e $z$ sono foglie sorelle.

## Algoritmo

Greedy ricorsivo: fonde le due lettere di minima frequenza in una meta-lettera $\omega$ con $f_\omega = f_y + f_z$, poi risolve ricorsivamente su $S' = S \setminus \{y,z\} \cup \{\omega\}$.

```
Huffman(S, f):
  if |S| = 2: codifica con 0 e 1
  else:
    y*, z* ← due lettere di minima frequenza
    ω ← meta-lettera con f_ω = f_{y*} + f_{z*}
    T' ← Huffman(S \ {y*,z*} ∪ {ω}, f')
    return T ottenuto da T' sostituendo ω con alberello (y*, z*)
```

**Lemma:** $\mathrm{ABL}(T') = \mathrm{ABL}(T) - f_\omega$.

**Teorema (correttezza):** Huffman restituisce il prefix-code di minima ABL. Dimostrazione per induzione su $|S|$ usando la relazione $\mathrm{ABL}(T) = f_\omega + \mathrm{ABL}(T')$.

## Complessità

- Naive: $O(n^2)$.
- Con priority queue (heap): $O(n \log n)$ — ogni fusione costa $O(\log n)$ e ci sono $n-1$ fusioni.

## Connessioni

- Paradigma: [[Algoritmo greedy]]
- Alberi binari: [[BFS e DFS]], [[Albero binario di ricerca]]
- Applicazione: compressione lossless (gzip, JPEG, ecc.)
- Discusso in: [[Algoritmi e Complessità]]

## Fonti

- [[Dispense Algoritmi — Galletti]] (§2.3-2.4, pp. 12-20)
