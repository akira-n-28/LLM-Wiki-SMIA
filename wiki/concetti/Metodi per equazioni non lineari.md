---
tipo: concetto
titolo: Metodi per equazioni non lineari
tag: [calcolo-numerico, metodi-numerici, analisi-numerica]
cluster: numerico
fonti: 1
ultima-modifica: 2026-05-05
---

# Metodi per equazioni non lineari

Dato $f: [a,b] \to \mathbb{R}$ continua, si cerca $x^* \in [a,b]$ tale che $f(x^*) = 0$ (**radice**). I metodi iterativi generano una successione $x_0, x_1, \ldots \to x^*$.

**Ordine di convergenza $p$:** $|e_{k+1}| \leq C|e_k|^p$ con $e_k = x_k - x^*$.
- $p=1$: convergenza lineare; $p=2$: quadratica (molto più veloce).

## Metodo di Bisezione

**Ipotesi:** $f(a)\cdot f(b) < 0$ (segni opposti → $\exists$ radice per il teorema degli zeri).

**Iterazione:** prendi il punto medio $c=(a+b)/2$; aggiorna l'intervallo dimezzando a sinistra o destra in base al segno di $f(c)$.

**Errore:** $|e_k| \leq \frac{b-a}{2^{k+1}}$

**Proprietà:**
- Converge sempre (non richiede alcuna ipotesi su $f'$).
- Ordine 1, fattore di riduzione $1/2$: lento ma affidabile.
- Non usa derivate.

## Metodo di Newton (Newton-Raphson)

$$x_{k+1} = x_k - \frac{f(x_k)}{f'(x_k)}$$

Interpreta geometricamente la tangente al grafico di $f$ in $(x_k, f(x_k))$.

**Convergenza quadratica** vicino a $x^*$ (se $f'(x^*) \neq 0$):

$$|e_{k+1}| \leq \frac{|f''(x^*)|}{2|f'(x^*)|}\,|e_k|^2 = M|e_k|^2$$

**Limiti:**
- Richiede $f'$ calcolabile analiticamente (o numericamente).
- Richiede $x_0$ sufficientemente vicino a $x^*$ (convergenza locale).
- Se $f'(x^*) = 0$ (radice multipla), l'ordine scende a 1.

## Metodo delle Secanti

$$x_{k+1} = x_k - f(x_k)\cdot\frac{x_k - x_{k-1}}{f(x_k) - f(x_{k-1})}$$

Approssima $f'$ con il rapporto incrementale. Non richiede la derivata analitica.

**Ordine:** $p = \phi = (1+\sqrt{5})/2 \approx 1.618$ (sezione aurea) — più lento di Newton ma non richiede $f'$.

## Metodo del Punto Fisso

Si riscrive $f(x)=0$ come $x = g(x)$ e si itera $x_{k+1} = g(x_k)$.

**Convergenza:** se $|g'(x^*)| < 1$, la successione converge con fattore asintotico $|g'(x^*)|$.

**Teorema di Banach-Caccioppoli:** se $g: [a,b]\to[a,b]$ è una contrazione ($|g'(x)| \leq L < 1$ su tutto l'intervallo), allora converge a un unico punto fisso. Vedi [[Teorema delle Contrazioni]].

**Relazione con Newton:** Newton è un caso speciale di punto fisso con $g(x) = x - f(x)/f'(x)$; poiché $g'(x^*)=0$, si ottiene convergenza di ordine 2.

## Confronto

| Metodo    | Ordine        | Richiede $f'$? | Convergenza globale? |
|-----------|---------------|----------------|----------------------|
| Bisezione | 1 (lenta)     | No             | Sì (con cambio di segno) |
| Secanti   | $\approx 1.62$| No             | Locale               |
| Newton    | 2             | Sì             | Locale               |
| Punto fisso | 1 (se $L<1$) | No            | Locale o globale     |

**Strategia pratica:** inizia con bisezione per avvicinarsi a $x^*$, poi switch a Newton per convergenza rapida.

## Connessioni

- Si collega a: [[Teorema delle Contrazioni]], [[Gradiente coniugato]], [[Metodo di Newton (ottimizzazione)]]
- Prerequisito di: [[Metodi numerici per ODE]] (per Eulero implicito)
- Discusso in: [[Metodi Numerici]]

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
