---
tipo: concetto
titolo: Cerchi di Gershgorin
tag: [algebra-lineare, calcolo-numerico, metodi-numerici, autovalori]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Cerchi di Gershgorin

I **cerchi di Gershgorin** localizzano lo spettro di $A \in \mathbb{C}^{n \times n}$ senza calcolare esplicitamente gli autovalori.

## Definizione

Per ogni $i = 1, \ldots, n$, il cerchio di Gershgorin della riga $i$ è:

$$C_i = \left\{z \in \mathbb{C} : |z - a_{ii}| \leq R_i\right\}, \quad R_i = \sum_{j \neq i} |a_{ij}|$$

Il centro è l'elemento diagonale $a_{ii}$; il raggio è la somma dei moduli degli off-diagonali nella riga $i$.

## Teorema di Gershgorin

$$\mathrm{spec}(A) \subseteq \bigcup_{i=1}^{n} C_i$$

Ogni autovalore di $A$ appartiene all'unione dei cerchi di Gershgorin.

**Dimostrazione (idea):** se $\lambda$ è autovalore con autovettore $v$, sia $i = \arg\max_j |v_j|$. Dalla $i$-esima riga di $Av = \lambda v$ si ricava $|\lambda - a_{ii}| \leq \sum_{j\neq i} |a_{ij}||v_j/v_i| \leq R_i$.

## Teorema di separazione

Se $k$ cerchi formano un insieme connesso $S$ separato dagli altri $n-k$ cerchi ($S \cap C_j = \emptyset$ per $j \notin S$), allora $S$ contiene **esattamente $k$ autovalori** (contati con molteplicità).

Questo permette di contare e separare autovalori senza calcolarli.

## Applicazioni

1. **Verifica dominanza diagonale:** $A$ è non-singolare se $0 \notin \bigcup_i C_i$, cioè se $|a_{ii}| > R_i$ per ogni $i$.

2. **Localizzazione rapida dello spettro:** utile per scegliere il parametro $\alpha_{\mathrm{opt}}$ del metodo di Richardson (che dipende da $[\lambda_{\min}, \lambda_{\max}]$).

3. **Stima di $K(A)$:** $K(A) = \lambda_{\max}/\lambda_{\min}$ (per SPD) può essere approssimato dai cerchi.

4. **Convergenza di Jacobi:** Jacobi converge garantito se $A$ è strettamente diagonalmente dominante, cioè se ogni $0$ è al di fuori di ogni $C_i$.

## Esempio

$$A = \begin{pmatrix} 4 & 1 & 0 \\ 1 & 6 & 2 \\ 0 & 2 & 5 \end{pmatrix}$$

Cerchi: $C_1 = \{|z-4|\leq 1\}$, $C_2 = \{|z-6|\leq 3\}$, $C_3 = \{|z-5|\leq 2\}$. Lo spettro è contenuto in $[3,5]\cup[3,9]$, quindi in $[3,9] \subset (0,\infty)$ — la matrice è definita positiva.

## Cerchi di Gershgorin per colonne

Il teorema si applica anche con i cerchi costruiti per colonne anziché righe (usando $A^T$), dando potenzialmente stime più strette.

## Connessioni

- Prerequisito di: [[Metodo delle potenze]], [[Algoritmo QR per autovalori]]
- Si collega a: [[Autovalori e autovettori]], [[Metodi iterativi per sistemi lineari]]
- Discusso in: [[Metodi Numerici]]

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
