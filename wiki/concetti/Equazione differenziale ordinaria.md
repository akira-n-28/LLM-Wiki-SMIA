---
tipo: concetto
titolo: Equazione differenziale ordinaria
tag: [mmf, equazioni-differenziali, analisi]
cluster: fisica
fonti: 2
ultima-modifica: 2026-05-06
---

# Equazione differenziale ordinaria (ODE)

Un'**ODE in una dimensione** è un problema del tipo:

$$\begin{cases} \dot{x} = f(x), \quad x \in \mathbb{R} \\ x(0) = x_0 \end{cases}$$

Il metodo di separazione delle variabili fornisce la soluzione formale: se $p'(x) = 1/f(x)$ allora $x(t) = p^{-1}(t + p(x_0))$.

Per $\dot{x} = f(x)$ con $x \in \mathbb{R}^n$, la **formulazione integrale equivalente** è:

$$x(t) = x_0 + \int_0^t f(x(s))\,ds$$

## Funzione Lipschitziana

**Definizione.** $f : \mathbb{R}^n \to \mathbb{R}^n$ è $L$-Lipschitz se $\exists L \geq 0$ tale che:

$$\|f(x) - f(y)\| \leq L\|x - y\| \quad \forall x, y$$

Proprietà: $C^1 \Rightarrow$ Lipschitz (con $L = \sup |f'|$). Le funzioni Lipschitziane sono uniformemente continue ma non necessariamente differenziabili (es. $f(x)=|x|$ è $1$-Lipschitz).

## Teorema di esistenza e unicità (Cauchy-Picard)

**Teorema.** Se $f$ è $L$-Lipschitz, il problema di Cauchy ammette **soluzione unica** per $t \in \mathbb{R}$.

**Dimostrazione.** Si costruisce la successione di Picard:

$$x_0(t) = x_0, \qquad x_{n+1}(t) = x_0 + \int_0^t f(x_n(s))\,ds$$

Con la norma $\|y\|_{0,T} = \max_{t \in [0,T]} |y(t)|$ si dimostra:

$$\|x_{n+1} - x_n\|_{0,T} \leq LT\,\|x_n - x_{n-1}\|_{0,T}$$

Scegliendo $T = \frac{1}{2L}$ si ottiene $\|x_{n+1}-x_n\| \leq \frac{1}{2}\|x_n - x_{n-1}\|$, la serie telescopica converge (serie di Cauchy), e il limite è l'unica soluzione.

## Lemma di Grönwall

**Lemma.** Siano $a, b \geq 0$ e $x(t)$ continua con $x(t) \leq a + b\int_0^t x(s)\,ds$. Allora:

$$x(t) \leq a e^{bt} \quad \forall t \geq 0$$

Strumento chiave per controllare la crescita di soluzioni perturbate.

## Dipendenza continua dal dato iniziale

**Teorema.** Se $f$ è $L$-Lipschitz e $x_1(t), x_2(t)$ sono soluzioni con dati iniziali $y_1, y_2$, allora:

$$|x_1(t) - x_2(t)| \leq e^{Lt}|y_1 - y_2| \quad \forall t > 0$$

Piccole perturbazioni del dato iniziale danno soluzioni vicine (su intervalli finiti di tempo). Conseguenza del lemma di Grönwall.

## Sistemi in più dimensioni

Per $\dot{z} = f(z)$ con $z = (x, v) \in \mathbb{R}^2$ (es. sistemi meccanici $m\ddot{x} = F(x)$):

$$\begin{cases} \dot{x} = v \\ \dot{v} = F(x)/m \end{cases}$$

Il comportamento qualitativo si studia analizzando le **curve di livello** dell'energia $H(x,v) = \frac{1}{2}mv^2 + U(x)$.

## Connessioni

- Applicazioni fisiche: [[Oscillatore armonico]], [[Stabilità di un punto di equilibrio]], [[Meccanica Lagrangiana]]
- Metodi numerici: [[Metodi numerici per ODE]]
- Teorema delle contrazioni (MetNum): [[Teorema delle Contrazioni]]
- Corsi: [[Modelli Matematici per la Fisica I]], [[Analisi Matematica I]] (intro §7)

## Fonti

- [[Dispense MMFI — Galletti]] (§1, pp. 1-8) — trattazione completa
- [[Dispense AnalisiI — Galletti]] (§7, pp. 154-163) — introduzione breve come applicazione del calcolo integrale
