---
tipo: concetto
titolo: Teorema delle Contrazioni
tag: [analisi, calcolo-numerico, matematica, metodi-numerici]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-05
---

# Teorema delle Contrazioni (Banach-Caccioppoli)

## Enunciato

Sia $(X, d)$ uno **spazio metrico completo** e $g: X \to X$ una **contrazione**, cioè:

$$\exists\, L \in [0,1): \quad d(g(x), g(y)) \leq L\, d(x,y) \quad \forall x,y \in X$$

Allora:
1. Esiste un **unico punto fisso** $x^* \in X$ tale che $g(x^*) = x^*$.
2. Per qualsiasi $x_0 \in X$, la successione $x_{k+1} = g(x_k)$ converge a $x^*$.

## Stima dell'errore

**A priori:**

$$d(x_k, x^*) \leq \frac{L^k}{1-L}\,d(x_1, x_0)$$

**A posteriori (più pratica):**

$$d(x_k, x^*) \leq \frac{L}{1-L}\,d(x_k, x_{k-1})$$

La stima a posteriori usa la distanza tra iterazioni consecutive, calcolabile senza conoscere $x^*$.

## Condizione sufficiente (su $\mathbb{R}$)

Se $g: [a,b] \to [a,b]$ è differenziabile e $|g'(x)| \leq L < 1$ per ogni $x \in [a,b]$, allora $g$ è una contrazione e il teorema si applica.

## Applicazioni in analisi numerica

### Punto fisso per equazioni non lineari
Si riscrive $f(x) = 0$ come $x = g(x)$ e si itera. Converge se $|g'(x^*)| < 1$ (convergenza locale).

### Metodo di Newton come contrazione
Per $g(x) = x - f(x)/f'(x)$, si ha $g'(x^*) = 0$ — Newton è una "super-contrazione" vicino alla radice, da cui la convergenza quadratica.

### Convergenza di Jacobi e Gauss-Seidel
La matrice di iterazione $G$ di un metodo iterativo definisce $g(x) = Gx + c$, che è una contrazione se $\|G\| < 1$ (condizione sufficiente) o equivalentemente $\rho(G) < 1$ (condizione necessaria e sufficiente).

### Metodi per ODE impliciti
Il metodo di Eulero implicito $x_{k+1} = x_k + h\,f(t_{k+1}, x_{k+1})$ si risolve con iterazioni di punto fisso; il teorema garantisce la convergenza se $h$ è piccolo abbastanza ($h \cdot L_f < 1$, con $L_f$ costante di Lipschitz di $f$).

## Connessioni

- Generalizza: convergenza dei [[Metodi iterativi per sistemi lineari]]
- Si applica a: [[Metodi per equazioni non lineari]], [[Metodi numerici per ODE]]
- Discusso in: [[Metodi Numerici]]

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
