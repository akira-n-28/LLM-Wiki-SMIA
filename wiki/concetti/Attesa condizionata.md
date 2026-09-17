---
tipo: concetto
titolo: Attesa condizionata
tag: [probabilità, fondamenti]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-06
---

# Attesa condizionata

L'**attesa condizionata** di una [[Variabile aleatoria]] $X$ dato un evento $A$ con $P(A) > 0$ è:

$$
E[X \mid A] = \sum_x x \cdot P(X = x \mid A) = \frac{1}{P(A)} \sum_{\omega \in A} X(\omega)\, P(\omega)
$$

(caso discreto; nel continuo si sostituiscono le somme con integrali).

## Attesa condizionata rispetto a una v.a.

Dato $Y$ v.a. discreta con valori in $\{y_1, y_2, \ldots\}$, si definisce $E[X \mid Y]$ come la **variabile aleatoria** che vale $E[X \mid Y = y_j]$ quando $Y = y_j$:

$$
E[X \mid Y](\omega) = \sum_j E[X \mid Y = y_j]\, \mathbf{1}_{\{Y = y_j\}}(\omega)
$$

Per ogni $\omega$, $E[X \mid Y]$ "guarda" $Y(\omega)$ e restituisce l'attesa di $X$ ristretta a quell'esito.

## Proprietà fondamentali

- **Linearità:** $E[aX + bZ \mid Y] = a\, E[X \mid Y] + b\, E[Z \mid Y]$.
- **Tower property** (legge dell'attesa totale):
  $$E[X] = E[\, E[X \mid Y]\,]$$
  Si "media via" $Y$ per ottenere l'attesa marginale.
- **Pull-out (take-out what is known)**: se $g(Y)$ è funzione di $Y$, allora $E[g(Y)\, X \mid Y] = g(Y)\, E[X \mid Y]$.
- **Indipendenza:** se $X \perp Y$, allora $E[X \mid Y] = E[X]$ (costante).
- **Idempotenza:** $E[\, E[X \mid Y] \mid Y\,] = E[X \mid Y]$.

## Formula di scomposizione (legge della varianza totale)

$$
\mathrm{Var}(X) = E[\mathrm{Var}(X \mid Y)] + \mathrm{Var}(E[X \mid Y])
$$

La varianza totale si scompone in **varianza intra-gruppo** + **varianza inter-gruppo**. Base statistica della **ANOVA**.

## Esempi

### Numero atteso di tentativi
Sia $T$ il numero di lanci di una moneta truccata (P(testa) = $p$) fino al primo successo. Condizionando sul primo lancio:
$$
E[T] = 1 \cdot p + (1 + E[T]) \cdot (1-p)
$$
Risolvendo: $E[T] = 1/p$ — è la geometrica.

### Random walk con barriera
$X_n$ random walk semplice; $\tau$ tempo di assorbimento. $E[\tau \mid X_0 = i]$ si calcola via condizionamento sul primo passo: $E[\tau \mid X_0 = i] = 1 + \tfrac{1}{2}E[\tau \mid X_0 = i-1] + \tfrac{1}{2}E[\tau \mid X_0 = i+1]$.

## Attesa condizionata e MMSE

Tra tutte le funzioni $g(Y)$, $E[X \mid Y]$ minimizza l'errore quadratico medio $E[(X - g(Y))^2]$. È il **migliore predittore** di $X$ basato su $Y$ in senso $L^2$:

$$
E[X \mid Y] = \arg\min_{g} E[(X - g(Y))^2]
$$

La regressione (lineare o non) è una *approssimazione* di questa quantità in una classe ristretta di $g$.

## Connessioni

- Generalizzazione: [[Probabilità condizionata]] su eventi → su σ-algebre (martingale, [[Catena di Markov]]).
- Usato per costruire [[Stimatore]] (Rao-Blackwell: condizionando su una statistica sufficiente si riduce la varianza).
- Base di [[Bilancio dettagliato]] e dell'analisi delle catene di Markov.
- In ML: la regressione $\mathbb{E}[Y \mid X]$ è il target ottimale del [[Rischio teorico]] con MSE.

## Persone

Concetto formalizzato da [[Kolmogorov, Andrey]] (1933) come integrale rispetto a una misura condizionata.

## Fonti

- [[Dispense ProbStat — Galletti]] (§3.2, p. 28)
