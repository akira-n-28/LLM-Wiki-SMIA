---
tipo: concetto
titolo: Metodi iterativi per sistemi lineari
tag: [calcolo-numerico, algebra-lineare, metodi-numerici]
cluster: numerico
fonti: 1
ultima-modifica: 2026-05-05
---

# Metodi iterativi per sistemi lineari

I **metodi iterativi** generano una successione $x^{(0)}, x^{(1)}, \ldots \to x^*$ (soluzione di $Ax=b$) tramite un'operazione a costo $O(n^2)$ per iterazione. Sono preferiti ai metodi diretti per sistemi grandi e sparsi.

## Schema generale

Si decompone $A = M - N$ con $M$ non singolare e "facile da invertire". L'iterazione è:

$$Mx^{(k+1)} = Nx^{(k)} + b \quad \Longleftrightarrow \quad x^{(k+1)} = M^{-1}N\,x^{(k)} + M^{-1}b$$

**Matrice di iterazione:** $G = M^{-1}N$. Convergenza $\Leftrightarrow \rho(G) < 1$ (raggio spettrale $< 1$).

Il residuo soddisfa $r^{(k)} = b - Ax^{(k)}$; l'errore decade come $\|e^{(k)}\| \approx \rho(G)^k \|e^{(0)}\|$.

## Metodo di Jacobi

**Splitting:** $M = D$ (diagonale di $A$), $N = -(L+U)$ (parti off-diagonali).

$$x_i^{(k+1)} = \frac{1}{a_{ii}}\left(b_i - \sum_{j \neq i} a_{ij} x_j^{(k)}\right)$$

Ogni componente si aggiorna usando solo i valori dell'iterazione precedente. Le $n$ componenti sono indipendenti → parallelizzabile.

**Convergenza garantita** se $A$ è **strettamente diagonalmente dominante**: $|a_{ii}| > \sum_{j\neq i}|a_{ij}|$ per ogni $i$.

## Metodo di Gauss-Seidel

**Splitting:** $M = D + L$ (triangolare inferiore), $N = -U$.

$$x_i^{(k+1)} = \frac{1}{a_{ii}}\left(b_i - \sum_{j < i} a_{ij} x_j^{(k+1)} - \sum_{j > i} a_{ij} x_j^{(k)}\right)$$

Usa immediatamente i valori aggiornati: converge in genere il doppio più veloce di Jacobi, ma non è parallelizzabile allo stesso modo.

**Convergenza garantita** anche per matrici SPD (non richiede dominanza diagonale stretta).

## Metodo di Richardson

**Forma:** $x^{(k+1)} = x^{(k)} + \alpha\, r^{(k)}$, dove $r^{(k)} = b - Ax^{(k)}$ è il residuo.

**Scelta ottimale del passo** (per $A$ SPD con autovalori in $[\lambda_1, \lambda_n]$, $\lambda_1 \leq \lambda_n$):

$$\alpha_{\mathrm{opt}} = \frac{2}{\lambda_1 + \lambda_n}, \qquad \rho_{\mathrm{opt}} = \frac{\lambda_n - \lambda_1}{\lambda_n + \lambda_1} = \frac{K(A) - 1}{K(A) + 1}$$

Con $K(A) \gg 1$: $\rho \approx 1 - 2/K(A)$ → convergenza molto lenta.

## Richardson precondizionato

Si introduce un precondizionatore $M \approx A$ e si risolve il sistema precondizionato:

$$M^{-1}Ax = M^{-1}b \quad \Rightarrow \quad K(M^{-1}A) \ll K(A)$$

$M$ deve essere facile da invertire (es. diagonale, ILU, SSOR). La scelta ottimale $M = A$ dà convergenza in 1 passo, ma è troppo costosa.

## Confronto

| Metodo         | Costo/iter. | Raggio spettrale $\rho$ | Note |
|----------------|-------------|-------------------------|------|
| Jacobi         | $O(n^2)$    | $\rho_J$               | parallelizzabile, lento |
| Gauss-Seidel   | $O(n^2)$    | $\rho_{GS} \approx \rho_J^2$ | 2× più veloce di Jacobi |
| Richardson (opt.) | $O(n^2)$ | $(K-1)/(K+1)$          | dipende forte da $K$ |
| Grad. coniugato | $O(n^2)$   | $(\sqrt{K}-1)/(\sqrt{K}+1)$ | ottimale per SPD |

**Nota:** il [[Gradiente coniugato]] (GC) usa residui come direzioni di discesa e converge molto più velocemente di Richardson: $\rho_{GC} = (\sqrt{K}-1)/(\sqrt{K}+1) \ll (K-1)/(K+1)$ per $K \gg 1$.

## Connessioni

- Prerequisito di: [[Gradiente coniugato]]
- Richiede: [[Numero di condizionamento]], [[Autovalori e autovettori]]
- Alternativa a: [[Sistemi lineari — metodi diretti]]
- Discusso in: [[Metodi Numerici]]

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
