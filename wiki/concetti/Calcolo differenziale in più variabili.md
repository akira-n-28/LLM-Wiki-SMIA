---
tipo: concetto
titolo: Calcolo differenziale in più variabili
tag: [analisi, matematica, analisi-2]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-06
---

# Calcolo differenziale in più variabili

## Derivate parziali e gradiente

Data $f:A\subseteq\mathbb{R}^N\to\mathbb{R}$ con $A$ aperto, la **derivata parziale** rispetto a $x_i$ è:
$$\frac{\partial f}{\partial x_i}(x) := \lim_{h\to 0}\frac{f(x_1,\ldots,x_i+h,\ldots,x_N)-f(x)}{h}$$

Il **gradiente** è il vettore delle derivate parziali:
$$\nabla f(x) = Df(x) = \left(\frac{\partial f}{\partial x_1}(x),\ldots,\frac{\partial f}{\partial x_N}(x)\right)$$

**Attenzione.** Derivabilità parziale $\not\Rightarrow$ continuità (es. $f(x,y)=xy/(x^2+y^2)$ è derivabile in $(0,0)$ ma non continua).

## Differenziabilità

$f$ è **differenziabile** in $x_0\in A$ se:
$$\lim_{h\to 0}\frac{f(x_0+h)-f(x_0)-\langle\nabla f(x_0),h\rangle}{|h|}=0$$

**Differenziale.** L'applicazione lineare $df(x_0):h\mapsto\langle\nabla f(x_0),h\rangle$ è il differenziale di $f$ in $x_0$.

**Implicazioni.** Differenziabilità $\Rightarrow$ continuità $\Rightarrow$ derivabilità parziale (ma nessuna freccia è invertibile).

**Teorema del differenziale.** Se le derivate parziali $\partial f/\partial x_i$ esistono e sono **continue** in un intorno di $x_0$, allora $f$ è differenziabile in $x_0$.

## Piano tangente

Se $f:A\subseteq\mathbb{R}^2\to\mathbb{R}$ è differenziabile in $(x_0,y_0)$, l'equazione del **piano tangente** al grafico è:
$$z = f(x_0,y_0) + f_x(x_0,y_0)(x-x_0) + f_y(x_0,y_0)(y-y_0)$$

In $\mathbb{R}^N$: **iperpiano tangente** $x_{N+1}=f(x_0)+\langle\nabla f(x_0),x-x_0\rangle$.

## Derivate direzionali

La **derivata direzionale** di $f$ in $x_0$ nella direzione $v\in\mathbb{R}^N$ ($|v|=1$) è:
$$D_v f(x_0) = \lim_{t\to 0}\frac{f(x_0+tv)-f(x_0)}{t}$$

Se $f$ è differenziabile: $D_v f(x_0) = \langle\nabla f(x_0), v\rangle$.

**Massima pendenza.** $\nabla f(x_0)$ punta nella direzione di massima crescita di $f$; $|{}\nabla f(x_0)|$ è il tasso di variazione massimo.

## Regola della catena

Se $g:\mathbb{R}^N\to\mathbb{R}$ e $\varphi:\mathbb{R}\to\mathbb{R}^N$ ($\varphi(t)=x_0+tv$), allora:
$$\frac{d}{dt}g(\varphi(t)) = \langle\nabla g(\varphi(t)), \varphi'(t)\rangle$$

Più in generale, per $f:A\subseteq\mathbb{R}^N\to\mathbb{R}$ e $g:B\subseteq\mathbb{R}^M\to A$:
$$\nabla(f\circ g)(x) = Dg(x)^T \nabla f(g(x))$$

**Funzioni con gradiente nullo.** Se $\nabla f=0$ su un aperto connesso, allora $f$ è costante.

## Polinomio di Taylor in $\mathbb{R}^N$

Sia $f\in C^2(A)$ e $x_0\in A$. **Formula di Taylor al 2° ordine** (resto di Peano):
$$f(x) = f(x_0) + \langle\nabla f(x_0), x-x_0\rangle + \frac{1}{2}\langle D^2f(x_0)(x-x_0), x-x_0\rangle + o(\|x-x_0\|^2)$$

La **matrice hessiana** è $D^2f(x_0) = \left(\frac{\partial^2 f}{\partial x_i\partial x_j}(x_0)\right)_{i,j}$.

Per $n=2$: il termine quadratico è $\frac{1}{2}[f_{xx}(x-x_0)^2 + 2f_{xy}(x-x_0)(y-y_0) + f_{yy}(y-y_0)^2]$.

Il teorema di Schwarz garantisce che se $f\in C^2$ allora $D^2f$ è **simmetrica**.

## Ottimizzazione libera

**Condizione necessaria del 1° ordine (Fermat).** Se $x_0$ è estremo relativo interno e $f$ è derivabile: $\nabla f(x_0)=0$.

I punti con $\nabla f=0$ si chiamano **punti stazionari/critici**; non sono necessariamente estremi (es. punti di sella $f(x,y)=x^2-y^2$).

**Condizione necessaria del 2° ordine.** Se $x_0$ è minimo relativo $\Rightarrow$ $D^2f(x_0)$ semidefinita positiva.

**Condizione sufficiente del 2° ordine.** Sia $\nabla f(x_0)=0$ e $f\in C^2$:
- $D^2f(x_0)$ definita positiva (tutti gli autovalori $>0$) $\Rightarrow$ **minimo locale**.
- $D^2f(x_0)$ definita negativa $\Rightarrow$ **massimo locale**.
- $D^2f(x_0)$ indefinita $\Rightarrow$ **punto di sella**.

*Dimostrazione:* Taylor al 2° ordine + stima $\langle D^2f(x_0)v,v\rangle\geq m|v|^2$ per $m>0$.

**Caso $n=2$ (criterio pratico).** Dato $D^2f=\begin{pmatrix}f_{xx}&f_{xy}\\f_{yx}&f_{yy}\end{pmatrix}$, si usa il discriminante $\Delta=f_{xx}f_{yy}-f_{xy}^2$:
- $\Delta>0$, $f_{xx}>0$ → minimo; $f_{xx}<0$ → massimo.
- $\Delta<0$ → sella.
- $\Delta=0$ → non conclusivo.

## Ottimizzazione su compatti

Se $f\in C^0(K)$ con $K\subseteq\mathbb{R}^N$ compatto, per Weierstrass esistono $\min_K f$ e $\max_K f$.

I punti estremi si cercano tra:
1. Punti critici interni ($\nabla f=0$).
2. Punti di non derivabilità.
3. Punti sulla frontiera $\partial K$ (problema ridotto di dimensione inferiore).

## Connessioni

- Prerequisito: [[Derivata]] (caso 1D), [[Limite di una funzione]] (in $\mathbb{R}^N$), [[Spazio metrico]]
- Ottimizzazione: [[Condizioni KKT]] (caso vincolato), [[Discesa del gradiente]] (applic. ML)
- Taylor in $\mathbb{R}^N$: usato in Newton, BFGS ([[Metodi Quasi-Newton]])

## Fonti

- [[Dispense AnalisiII — Galletti]] (§3, pp. 38-69)
