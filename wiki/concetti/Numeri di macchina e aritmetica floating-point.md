---
tipo: concetto
titolo: Numeri di macchina e aritmetica floating-point
tag: [calcolo-numerico, metodi-numerici, aritmetica]
cluster: numerico
fonti: 1
ultima-modifica: 2026-05-05
---

# Numeri di macchina e aritmetica floating-point

I **numeri di macchina** $\mathbb{F}$ sono un sottoinsieme finito di $\mathbb{R}$. Ogni numero in $\mathbb{F}$ ha la forma:

$$x = \pm m \cdot \beta^e$$

dove $\beta$ è la base, $m$ è la mantissa con $t$ cifre, ed $e$ è l'esponente con range $[e_{\min}, e_{\max}]$.

## Standard IEEE 754

| Formato   | Bit totali | Mantissa | Esponente | $\varepsilon_M$                    |
|-----------|------------|----------|-----------|------------------------------------|
| `float32` | 32         | 23 bit   | 8 bit     | $\approx 1.2 \times 10^{-7}$      |
| `float64` | 64         | 52 bit   | 11 bit    | $\approx 2.2 \times 10^{-16}$     |

**Precisione di macchina** $\varepsilon_M$: il più piccolo numero tale che $\mathrm{fl}(1 + \varepsilon_M) > 1$.

## Arrotondamento

La funzione di arrotondamento $\mathrm{fl}: \mathbb{R} \to \mathbb{F}$ soddisfa:

$$\mathrm{fl}(x) = x(1 + \delta), \quad |\delta| \leq \frac{\varepsilon_M}{2}$$

L'errore relativo introdotto da ogni operazione elementare è al più $\varepsilon_M/2$.

## Overflow e Underflow

- **Overflow** ($|x| > \mathrm{OFL}$): il risultato eccede il massimo rappresentabile; produce $\pm\infty$.
- **Underflow** ($|x| < \mathrm{UFL}$, senza denormalizzati): il risultato viene troncato a 0.

## Cancellazione catastrofica

Si verifica quando si sottraggono due numeri quasi uguali: $a - b$ con $a \approx b$.

**Esempio:** $a = 1.000001$, $b = 1.000000$. La differenza è $10^{-6}$, ma si perdono fino a 6 cifre significative di $a$ e $b$.

L'errore relativo sul risultato può essere amplificato di un fattore $|a|/(|a-b|)$.

**Rimedio:** riscrivere l'espressione per evitare la sottrazione, o cambiare l'ordine delle operazioni.

Esempio: calcolo di $\sum_{n=1}^{N} \frac{1}{n^2}$ — sommare da $n=N$ a $n=1$ (termini piccoli prima) riduce l'errore di accumulo.

## Propagazione degli errori

Per un'operazione $f(x,y)$, l'errore relativo si propaga come:

$$\frac{|\Delta f|}{|f|} \approx \frac{|x f_x|}{|f|}\frac{|\Delta x|}{|x|} + \frac{|y f_y|}{|f|}\frac{|\Delta y|}{|y|}$$

I coefficienti $|x f_x/f|$ e $|y f_y/f|$ sono i **numeri di condizionamento del problema**.

## Stabiltà di un algoritmo

Un algoritmo è **stabile** se l'errore introdotto è proporzionale a $\varepsilon_M$ (non amplificato). La fattorizzazione di Gauss senza pivoting può essere instabile; con pivoting parziale è in pratica stabile.

## Connessioni

- Prerequisito di: [[Sistemi lineari — metodi diretti]], [[Metodi iterativi per sistemi lineari]], [[Integrazione numerica]]
- Si collega a: [[Numero di condizionamento]]
- Discusso in: [[Metodi Numerici]]

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
