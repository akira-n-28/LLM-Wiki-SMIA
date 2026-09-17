---
tipo: concetto
titolo: Curve e integrali curvilinei
tag: [analisi, matematica, analisi-2]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-06
---

# Curve e integrali curvilinei

## Curve in $\mathbb{R}^N$

Una **curva** è un'applicazione continua $\varphi:[a,b]\to\mathbb{R}^N$. L'immagine $\varphi([a,b])$ si chiama **sostegno** (o traiettoria) della curva.

**Curva regolare.** $\varphi$ è regolare se:
1. $\varphi\in C^1([a,b])$ (componenti derivabili con derivata continua),
2. $\varphi'(t)\neq 0\ \forall t\in[a,b]$.

Il vettore $\varphi'(t)$ è il **vettore velocità**, tangente alla traiettoria in $\varphi(t)$.

**Curva regolare a tratti.** Unione finita di curve regolari.

## Lunghezza di una curva

Per una partizione $P$ di $[a,b]$, la poligonale iscritta ha lunghezza $L(P)=\sum_i|\varphi(t_i)-\varphi(t_{i-1})|$.

La **lunghezza** di $\varphi$ è $L(\varphi)=\sup_P L(P)$. Se $L(\varphi)<+\infty$ la curva è **rettificabile**.

**Teorema.** Se $\varphi\in C^1([a,b])$:
$$L(\varphi) = \int_a^b|\varphi'(t)|\,dt = \int_a^b\sqrt{\varphi_1'(t)^2+\cdots+\varphi_N'(t)^2}\,dt$$

## Integrale curvilineo di prima specie

Misura quantità del tipo "somma di $f$ lungo la curva pesata dall'elemento di lunghezza $ds=|\varphi'(t)|\,dt$":
$$\int_\gamma f\,ds = \int_a^b f(\varphi(t))|\varphi'(t)|\,dt$$

Richiede $f$ continua sul sostegno. **Non dipende dalla parametrizzazione** (invariante per riparametrizzazione a senso crescente).

*Esempio.* La lunghezza è $\int_\gamma 1\,ds = L(\varphi)$.

## Forme differenziali e integrali di II specie

Una **forma differenziale** in $\mathbb{R}^N$ è $\omega=F_1\,dx_1+\cdots+F_N\,dx_N$ con $F_i:A\to\mathbb{R}$.

L'**integrale di II specie** di $\omega$ lungo $\gamma=\varphi([a,b])$ (con verso) è:
$$\int_\gamma\omega = \int_\gamma F\cdot d\ell = \int_a^b\langle F(\varphi(t)),\varphi'(t)\rangle\,dt$$

Dipende dall'orientazione: cambiando verso, l'integrale cambia segno.

*Interpretazione fisica.* Se $F$ è un campo di forze, $\int_\gamma F\cdot d\ell$ è il lavoro compiuto lungo $\gamma$.

## Differenziale di una funzione $C^1$

Se $U:A\subseteq\mathbb{R}^N\to\mathbb{R}$ è di classe $C^1$, il suo **differenziale** è:
$$dU = \frac{\partial U}{\partial x_1}\,dx_1+\cdots+\frac{\partial U}{\partial x_N}\,dx_N$$

È la forma differenziale che corrisponde al gradiente di $U$.

## Forme differenziali esatte

$\omega=\sum F_i\,dx_i$ è **esatta** su $A$ se esiste $U\in C^1(A)$ (potenziale) con $\omega=dU$, cioè $F_i=\partial U/\partial x_i$.

**Proprietà fondamentale.** Se $\omega=dU$ e $\gamma$ è una curva da $A$ a $B$:
$$\int_\gamma\omega = U(B)-U(A)$$

L'integrale dipende solo dagli estremi, non dalla curva (indipendenza dal cammino).

**Condizione necessaria per l'esattezza.** Se $\omega=P\,dx+Q\,dy$ è esatta su $A$ aperto:
$$\frac{\partial P}{\partial y}=\frac{\partial Q}{\partial x}$$

(Condizione necessaria perché $\partial^2 U/\partial y\partial x = \partial^2 U/\partial x\partial y$.)

**Condizione sufficiente.** Su un dominio **semplicemente connesso** (senza buchi), $\partial P/\partial y=\partial Q/\partial x$ $\Leftrightarrow$ $\omega$ è esatta.

**Calcolo del potenziale.** Dato che $\partial U/\partial x = P$: $U(x,y)=\int P\,dx+g(y)$, poi si determina $g$ imponendo $\partial U/\partial y = Q$.

## Connessioni

- Prerequisito: [[Integrale di Riemann]] (integrale 1D), [[Calcolo differenziale in più variabili]] (gradiente, differenziale)
- Integrali su superfici (Analisi III): estensione naturale
- Lavoro e campi conservativi ([[Meccanica Lagrangiana]])
- Teorema di Green/Stokes/Gauss: collegamento tra integrali di I e II specie

## Fonti

- [[Dispense AnalisiII — Galletti]] (§6, pp. 118-130)
