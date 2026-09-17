---
tipo: concetto
titolo: Oscillatore armonico
tag: [mmf, meccanica, equazioni-differenziali]
cluster: fisica
fonti: 1
ultima-modifica: 2026-05-06
---

# Oscillatore armonico

Descrive il moto di un punto materiale soggetto a una forza proporzionale allo spostamento (legge di Hooke):

$$m\ddot{x} = -kx$$

**Sistema equivalente:**

$$\begin{cases} \dot{x} = v \\ \dot{v} = -\tfrac{k}{m}x \end{cases}$$

## Soluzione generale

Polinomio caratteristico: $m\lambda^2 + k = 0 \Rightarrow \lambda = \pm i\omega$ con $\omega = \sqrt{k/m}$.

$$x(t) = A\cos(\omega t + \varphi) = x_0\cos(\omega t) + \frac{v_0}{\omega}\sin(\omega t)$$

**Periodo:** indipendente dall'ampiezza,

$$T = \frac{2\pi}{\omega} = 2\pi\sqrt{\frac{m}{k}}$$

## Conservazione dell'energia

L'**Hamiltoniana**:

$$H(x,v) = \frac{1}{2}mv^2 + \frac{1}{2}kx^2 = E = \text{costante}$$

si conserva lungo le soluzioni. Le orbite nel piano delle fasi $(x,v)$ sono **ellissi** di semiassi $a = \sqrt{2E/k}$ e $b = \sqrt{2E/m}$.

**Analisi qualitativa:**
- $E < 0$: non ci sono moti
- $E = 0$: unico punto di equilibrio stabile $(0,0)$
- $E > 0$: moto periodico

## Pendolo semplice

L'equazione $ml\ddot{\theta} = -mg\sin\theta$ porta a $\ddot{\theta} = -\frac{g}{l}\sin\theta$ con $U(\theta) = \frac{g}{l}(1-\cos\theta)$.

**Analisi qualitativa per $E < \bar{U} = 2g/l$:** orbite periodiche chiuse.  
**Per $E = \bar{U}$:** separatrice; per $E > \bar{U}$: orbite illimitate (rotazione continua).

**Teorema di Galileo.** Per $E \to \bar{U}^+$ il periodo tende a:

$$T \to 2\pi\sqrt{\frac{m}{U''(\bar{x})}}$$

Per piccole oscillazioni del pendolo: $T \approx 2\pi\sqrt{l/g}$.

## Oscillatore smorzato

Aggiungendo attrito: $\dot{v} = -x - \lambda v \Rightarrow \frac{d}{dt}H = -\lambda v^2 \leq 0$. Il sistema è **dissipativo** (perde energia).

## Oscillatore di Van der Pol

$$\begin{cases} \dot{x} = y \\ \dot{y} = -x + \varepsilon(1-x^2)y \end{cases}$$

Per $\varepsilon = 0$: orbite circolari. Per $\varepsilon \neq 0$ piccolo: esiste un **ciclo limite** stabile di raggio $\bar{u} = 2$ (via teorema di Poincaré-Bendixson). Il sistema acquista o cede energia a seconda di $|x| \lessgtr 1$.

## Connessioni

- Generalizzazione: [[Meccanica Lagrangiana]], [[Stabilità di un punto di equilibrio]]
- Teoria ODE sottostante: [[Equazione differenziale ordinaria]]
- Connessione numerica: [[Metodi numerici per ODE]]
- Corsi: [[Modelli Matematici per la Fisica I]]

## Fonti

- [[Dispense MMFI — Galletti]] (§2, pp. 6-25)
