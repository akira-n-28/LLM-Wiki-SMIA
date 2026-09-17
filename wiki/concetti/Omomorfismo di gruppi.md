---
tipo: concetto
titolo: Omomorfismo di gruppi
tag: [algebra, matematica, strutture-algebriche]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Omomorfismo di gruppi

Un **omomorfismo** tra gruppi $(G, \cdot)$ e $(K, \star)$ è una funzione $f: G \to K$ tale che:

$$f(a \cdot b) = f(a) \star f(b) \quad \forall a, b \in G$$

In altre parole, $f$ preserva l'operazione di gruppo.

## Proprietà immediate

Da $f(a \cdot b) = f(a) \star f(b)$ si deduce:
- $f(e_G) = e_K$ (l'omomorfismo manda neutro in neutro)
- $f(a^{-1}) = f(a)^{-1}$ (preserva gli inversi)
- $f(a^n) = f(a)^n$ per ogni $n \in \mathbb{Z}$

## Tipi di omomorfismi

| Nome | Condizione |
|---|---|
| **Monomorfismo** (iniettivo) | $f$ iniettiva |
| **Epimorfismo** (suriettivo) | $f$ suriettiva |
| **Isomorfismo** | $f$ biettiva; si scrive $G \cong K$ |
| **Endomorfismo** | $G = K$ |
| **Automorfismo** | $G = K$ e $f$ biettiva |

Il gruppo degli automorfismi di $G$ si denota $\mathrm{Aut}(G)$.

## Nucleo e immagine

$$\ker(f) = \{g \in G \mid f(g) = e_K\}$$
$$\mathrm{Im}(f) = \{f(g) \mid g \in G\} \subseteq K$$

**Proprietà fondamentali:**
- $\ker(f) \unlhd G$ (il nucleo è sempre un [[Sottogruppo]] **normale**)
- $\mathrm{Im}(f) \leq K$ (l'immagine è un sottogruppo di $K$)
- $f$ iniettiva $\Leftrightarrow$ $\ker(f) = \{e_G\}$

## Primo teorema di isomorfismo

$$G / \ker(f) \cong \mathrm{Im}(f)$$

Il gruppo quoziente $G/N$ (per $N \unlhd G$) è l'insieme delle classi laterali $\{gN\}$ con operazione $(gN)(g'N) = (gg')N$. La proiezione $\pi: G \to G/N$, $g \mapsto gN$, è un epimorfismo con $\ker(\pi) = N$.

## Esempi

- $\exp: (\mathbb{R}, +) \to (\mathbb{R}_{>0}, \cdot)$, $x \mapsto e^x$: isomorfismo.
- $\det: (GL_n(\mathbb{R}), \cdot) \to (\mathbb{R}^*, \cdot)$: epimorfismo, $\ker(\det) = SL_n(\mathbb{R}) \unlhd GL_n(\mathbb{R})$.
- Segno $\epsilon: S_n \to \{+1,-1\}$: epimorfismo (per $n \geq 2$), $\ker(\epsilon) = A_n \unlhd S_n$.
- $\pi: \mathbb{Z} \to \mathbb{Z}_n$, $k \mapsto [k]_n$: epimorfismo, $\ker = n\mathbb{Z}$; da cui $\mathbb{Z}/n\mathbb{Z} \cong \mathbb{Z}_n$.

## Connessioni

- Prerequisito: [[Gruppo (struttura algebrica)]], [[Sottogruppo]]
- Nucleo e normalità: [[Sottogruppo]] (§ sottogruppo normale)
- Applicazione a $S_n$: [[Gruppo simmetrico]], [[Permutazione]]
- Classi quoziente: [[Teorema di Lagrange]]
- In [[Mappe lineari]] per spazi vettoriali (analogo lineare)
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§3.4, pp. 109-117)
