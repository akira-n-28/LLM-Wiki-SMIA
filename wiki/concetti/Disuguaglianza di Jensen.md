---
tipo: concetto
titolo: Disuguaglianza di Jensen
tag: [probabilità, analisi, ml]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Disuguaglianza di Jensen

Sia `φ: ℝ → ℝ` una funzione **convessa** e `X` una variabile aleatoria. Allora:

$$
\mathbb{E}[\varphi(X)] \geq \varphi(\mathbb{E}[X])
$$

Se `φ` è **strettamente convessa** e `X` non è degenere (non concentrata in un punto), vale la disuguaglianza stretta:

$$
\mathbb{E}[\varphi(X)] > \varphi(\mathbb{E}[X])
$$

Per funzioni **concave** il verso si inverte: `E[φ(X)] ≤ φ(E[X])`.

## Casi utili

- `φ(x) = x²` (convessa stretta): `E[X²] ≥ (E[X])²`, che è `Var(X) ≥ 0`.
- `φ(x) = e^x` (convessa): `E[e^X] ≥ e^{E[X]}`.
- `φ(x) = -\log x` (convessa per `x > 0`): `E[-\log X] ≥ -\log E[X]` → non-negatività della KL.
- `φ(x) = \log x` (concava): `E[\log X] ≤ \log E[X]`.

## Uso 1: non-negatività della KL

La [[Divergenza di Kullback-Leibler|disuguaglianza di Gibbs]] `D_KL(P ‖ Q) ≥ 0` segue da Jensen applicato a `-log`:

$$
D_{KL}(P \| Q) = \mathbb{E}_P\!\left[-\log \frac{Q(X)}{P(X)}\right] \geq -\log \mathbb{E}_P\!\left[\frac{Q(X)}{P(X)}\right] = -\log 1 = 0
$$

## Uso 2: monotonia dell'evidenza Bayesiana

Nel framework [[Apprendimento Bayesiano|Bayesiano]], la sequenza delle evidenze `L_t = E_{w_{t-1}}[g(τ|θ)]` è strettamente crescente. Il passo chiave usa Jensen con `φ(x) = x²`:

$$
E_{w_{t-1}}[g^2(\tau|\theta)] > \bigl(E_{w_{t-1}}[g(\tau|\theta)]\bigr)^2 = L_{t-1}^2
$$

da cui `L_t = E_{w_{t-1}}[g^2(\tau|\theta)] / L_{t-1} > L_{t-1}`.

## Uso 3: termine di varianza nella decomposizione bias-varianza (BIC)

La decomposizione del rischio in apprendimento non supervisionato ha un termine di varianza:

$$
\mathbb{E}_T\!\left[\int f(\tau') \log \frac{\bar g(\tau')}{g(\tau'|T)}\,d\tau'\right] \geq 0
$$

la non-negatività segue da Jensen applicato a `log` (concava), ovvero `E[\log X] ≤ \log E[X]`.

## Dimostrazione elementare (caso discreto)

Per `φ` convessa, esiste una retta di supporto in ogni punto: `φ(y) ≥ φ(µ) + φ'(µ)(y - µ)` per ogni `y`, con `µ = E[X]`. Prendendo il valore atteso entrambi i lati:

$$
E[\varphi(X)] \geq \varphi(\mu) + \varphi'(\mu)\underbrace{E[X - \mu]}_{=0} = \varphi(E[X])
$$

## Collegamento con la convessità della funzione di perdita

La convessità compare anche nell'[[Errore di approssimazione e di stima]]: l'errore statistico `E[(g_τ^G - g^G)²] ≥ 0` è banalmente non negativo, ma il legame con Jensen emerge nel caso Bayesiano.

## Collegamento con la formula di Gibbs (fisica statistica)

In fisica, la distribuzione di Boltzmann-Gibbs minimizza la energia libera — un risultato legato alla convessità dell'entropia. Vedi [[Metodi Monte Carlo]].

## Collegamenti

- Usato per: [[Divergenza di Kullback-Leibler]] (non-negatività), [[Apprendimento Bayesiano]] (monotonia evidenza), [[BIC]] (decomposizione)
- Variante per log: disuguaglianza di Gibbs
- Contesto fisico: [[Metodi Monte Carlo]]
- Persona: [[Jensen, Johan]]

## Fonti

- [[Dispense MatML — Galletti]] (§2.10-2.11, definizione 2.7, pp. 32-33, 41)
