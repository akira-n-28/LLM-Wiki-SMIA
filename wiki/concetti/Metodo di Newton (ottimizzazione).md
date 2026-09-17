---
tipo: concetto
titolo: Metodo di Newton (ottimizzazione)
tag: [ottimizzazione, algoritmi, analisi-numerica]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Metodo di Newton (ottimizzazione)

Metodo del secondo ordine per minimizzare $f \in C^2(\mathbb{R}^n)$ che sfrutta la Hessiana $\nabla^2 f$. Converge **localmente** con velocità superlineare o quadratica, ma inapplicabile direttamente a larga scala (costo $O(n^3)$ per iterazione).

## Derivazione (approssimazione quadratica)

Dati $x_k$ e uno spostamento $s$, approssimiamo:
$$
f(x_k + s) \approx q_k(s) = f(x_k) + \nabla f(x_k)^T s + \tfrac12 s^T \nabla^2 f(x_k) s
$$

Minimizzando $q_k(s)$ rispetto a $s$ (se $\nabla^2 f(x_k) \succ 0$):
$$
\nabla q_k(s) = \nabla^2 f(x_k) s + \nabla f(x_k) = 0 \quad \Rightarrow \quad s_k = -[\nabla^2 f(x_k)]^{-1} \nabla f(x_k)
$$

$$
\boxed{x_{k+1} = x_k - [\nabla^2 f(x_k)]^{-1} \nabla f(x_k)}
$$

## Connessione con sistemi non lineari

Cercare $\min f(x)$ equivale a risolvere $\nabla f(x) = 0$ (sistema non lineare). Il metodo di Newton per $F(x) = \nabla f(x) = 0$ è:
$$
x_{k+1} = x_k - [J_F(x_k)]^{-1} F(x_k) = x_k - [\nabla^2 f(x_k)]^{-1} \nabla f(x_k)
$$

**Teorema (convergenza locale)**: se $F \in C^1(D)$, $\exists x^*: F(x^*) = 0$, $J(x^*)$ non singolare, allora $\exists B(x^*, l)$ tale che per $x_0 \in B(x^*, l)$ la successione converge a $x^*$ con velocità **superlineare**. Se $J$ è Lipschitz-continua ($\|J(x)-J(y)\| \leq L\|x-y\|$), la convergenza è **quadratica**.

## Problemi pratici

1. $\nabla^2 f(x_k)$ **singolare** → il sistema $\nabla^2 f(x_k) s = -\nabla f(x_k)$ non ha soluzione unica.
2. $\{x_k\}$ non ammette punti limite.
3. $x_k \to x^*$ con $\nabla f(x^*) = 0$ ma $\nabla^2 f(x^*)$ definita negativa (massimo locale, non minimo).
4. **Solo convergenza locale**: richiede $x_0$ vicino alla soluzione.

## Versione robusta

Si risolve il sistema lineare $\nabla^2 f(x_k) d = -\nabla f(x_k)$ per $d_k^N$. Se la direzione soddisfa la condizione d'angolo e $d_k^N$ è di discesa, si pone $d_k = d_k^N$. Altrimenti si ripristina l'antigradiente:
$$
d_k = \begin{cases} d_k^N & \text{se } d_k^N \text{ è di discesa e soddisfa cond. d'angolo} \\ -\nabla f(x_k) & \text{altrimenti} \end{cases}
$$
Poi $x_{k+1} = x_k + \alpha_k d_k$ con $\alpha_k$ da [[Metodo di Armijo]].

## Newton troncato (larga scala)

Per $n \geq 10^4$ non si calcola $\nabla^2 f$ esplicitamente né si risolve il sistema esattamente. Si usa il [[Gradiente coniugato]] con criterio d'arresto per risolvere approssimativamente $\nabla^2 f(x_k) d = -\nabla f(x_k)$.

Il prodotto Hessiana-vettore si approssima con differenze finite:
$$
\nabla^2 f(x_k) v \approx \frac{\nabla f(x_k + \varepsilon v) - \nabla f(x_k)}{\varepsilon}
$$
senza mai formare la matrice $n \times n$.

## Confronto con [[Gradiente coniugato]]

| Aspetto | Newton | CG non lineare |
|---|---|---|
| Info usate | $f, \nabla f, \nabla^2 f$ | $f, \nabla f$ |
| Costo/iter | $O(n^3)$ (solve sistema) | $O(n)$ |
| Convergenza | locale, quadratica | globale, superlineare (con Wolfe) |
| Uso | problemi piccoli/medi | larga scala, reti neurali |

## Collegamento con i corsi

- [[Ottimizzazione]]: §4.3.
- [[Metodi Numerici]]: radici di sistemi non lineari $F(x)=0$.
- [[Matematica per il Machine Learning]]: [[Apprendimento Bayesiano]] usa approssimazione di Laplace basata su Newton.

## Fonti

- [[Dispense Ottimizzazione — Galletti]] (§4.3, pp. 36-38)
