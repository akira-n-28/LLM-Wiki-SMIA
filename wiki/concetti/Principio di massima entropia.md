---
tipo: concetto
titolo: Principio di massima entropia
tag: [mmf, probabilità, fisica-statistica, teoria-dell-informazione]
cluster: fisica
fonti: 1
ultima-modifica: 2026-05-06
---

# Principio di massima entropia (MaxEnt)

**Principio.** Data un'osservazione parziale del sistema (un insieme di vincoli $\mathbb{E}[g_\alpha(X)] = \bar{g}_\alpha$), la distribuzione che massimizza l'entropia è quella che fa il minor numero di assunzioni aggiuntive.

## Schema generale

Si massimizza l'**entropia di Gibbs** $S[p] = -\sum_x p_x \log p_x$ con vincoli:

$$\sum_x p_x = 1, \qquad \sum_x p_x g_\alpha(x) = \bar{g}_\alpha \quad \alpha = 1,\ldots,K$$

Via moltiplicatori di Lagrange ($\lambda_0, \lambda_1, \ldots, \lambda_K$), la soluzione è sempre della forma:

$$\boxed{p_x = \frac{1}{Z}\exp\!\left(\sum_\alpha \lambda_\alpha g_\alpha(x)\right)}$$

con **funzione di partizione** $Z = \sum_x \exp(\sum_\alpha \lambda_\alpha g_\alpha(x))$ (normalizzazione).

I $\lambda_\alpha$ si determinano imponendo i vincoli $\mathbb{E}[g_\alpha] = \bar{g}_\alpha$, che equivale a:

$$\frac{\partial}{\partial \lambda_\alpha}\log Z = \bar{g}_\alpha, \qquad \frac{\partial^2}{\partial \lambda_\alpha^2}\log Z = \text{Var}[g_\alpha]$$

## Distribuzioni di massima entropia per vincoli tipici

| Vincoli noti | Distribuzione MaxEnt |
|---|---|
| Nessuno | Uniforme su $\Omega$ |
| $\mathbb{E}[X] = \mu$ (discreto) | Esponenziale geometrica |
| $\mathbb{E}[X] = \mu$ (continuo, $x\geq 0$) | Esponenziale |
| $\mathbb{E}[X] = \mu$, $\text{Var}(X) = \sigma^2$ | Gaussiana $\mathcal{N}(\mu,\sigma^2)$ |

## Distribuzione di Boltzmann

In fisica statistica, il vincolo naturale è l'**energia media** $\mathbb{E}[H(\sigma)] = \bar{E}$:

$$p(\sigma) = \frac{e^{-\beta H(\sigma)}}{Z}, \quad Z = \sum_\sigma e^{-\beta H(\sigma)}, \quad \beta = \frac{1}{T}$$

(Temperatura $T$ come moltiplicatore di Lagrange per il vincolo sull'energia.) Questa è la **distribuzione di Boltzmann-Gibbs**.

**Energia libera:** $F = -T\log Z$, con $\mathbb{E}[H] = \partial(\beta F)/\partial\beta$ e $S = -\partial F/\partial T$.

## Entropia in funzione dei moltiplicatori

$$S = -\sum_x p_x \log p_x = -\sum_\alpha \lambda_\alpha \bar{g}_\alpha + \log Z$$

equivalente a: $S = \log Z + \Omega(u)$ nel linguaggio delle grandi deviazioni.

## Connessioni

- Concetto base: [[Entropia di Shannon]]
- Applicazione fisica: [[Modello di Ising]], [[Modello di Curie-Weiss e Hopfield]]
- Moltiplicatori: [[Condizioni KKT]] (analogo per ottimizzazione)
- Corsi: [[Modelli Matematici per la Fisica II]]

## Fonti

- [[Dispense MMFII — Galletti]] (§3, pp. 27-32)
