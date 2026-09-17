---
tipo: fonte
titolo: Dispense AnalisiII — Galletti
autori: [Marco Galletti]
docente-corso: Giulio Galise
anno-accademico: 2024/2025
data-ingest: 2026-05-06
file-raw: raw/appunti/analisi2.pdf
pagine: 130
ultima-modifica: 2026-05-06
tag: [matematica, analisi]
---

# Dispense di Analisi Matematica II — Galletti

**Riferimento file raw:** `raw/appunti/analisi2.pdf`
**Corso:** [[Analisi Matematica II]] (prof. Giulio Galise, A.A. 2024/2025, SMIA Sapienza)
**Autore appunti:** [[Galletti, Marco]]

## Riassunto in 5 punti

1. **Successioni/serie di funzioni**: convergenza puntuale vs uniforme (e perché conta), serie di potenze, raggio di convergenza (Cauchy-Hadamard), sviluppabilità in serie di Taylor.
2. **Spazi metrici**: metrica, topologia, completezza, successioni di Cauchy, spazi normati, prodotto scalare, spazi di Banach; Cauchy-Schwarz in $\mathbb{R}^N$.
3. **Calcolo differenziale in $\mathbb{R}^N$**: derivate parziali, gradiente, differenziabilità (e differenza con derivabilità parziale), piano tangente, Taylor 2° ordine con Hessiana, ottimizzazione libera (criteri I e II ordine, punti di sella) e vincolata su compatti.
4. **Integrale di Lebesgue**: misura, funzioni misurabili, teoremi di convergenza (Beppo Levi, Fatou, dominata di Lebesgue), derivazione sotto il segno, Fubini/Tonelli, integrali su domini normali, cambi di variabile (polari, sferiche, cilindriche).
5. **Spazi $L^p$ e curve**: $L^p(E)$ come spazi di Banach, Young/Hölder/Minkowski, $L^\infty$; curve regolari, lunghezza, integrali I e II specie, forme differenziali esatte (potenziale).

## Argomenti trattati

### §1 Successioni e serie di funzioni (pp. 2-26)
- Convergenza puntuale (il $\nu$ dipende da $x$) vs convergenza uniforme ($\sup|f_n-f|\to 0$)
- Proprietà della conv. uniforme: continuità, integrabilità, derivabilità della funzione limite
- M-test di Weierstrass per serie di funzioni
- Serie di potenze $\sum a_n x^n$; raggio di convergenza $\varphi$ (Cauchy-Hadamard: $\varphi=1/\limsup\sqrt[n]{|a_n|}$)
- Convergenza uniforme su $[x_0-r,x_0+r]$ per $r<\varphi$; derivazione/integrazione termine a termine
- Sviluppabilità in serie di Taylor: criterio (resto di Lagrange $\to 0$); funzioni $C^\infty$ non analitiche

### §2 Spazi metrici (pp. 27-37)
- Definizione $(X,d)$; esempi: euclidea in $\mathbb{R}^N$, Manhattan, $C^0([a,b])$ con $d_\infty$ e $d_1$
- Disuguaglianza di Cauchy-Schwarz in $\mathbb{R}^N$ (dim. via polinomio di 2° grado)
- Topologia: palle, aperti, chiusi, punti di accumulazione, chiusura, frontiera
- Successioni: convergenza $\Leftrightarrow d(x_n,x)\to 0$; coordinatewise in $\mathbb{R}^N$; uniformemente in $C^0$
- Completezza: successioni di Cauchy; $\mathbb{R}^N$ e $(C^0,d_\infty)$ sono completi; $(C^0,d_1)$ non è completo
- Norme su $\mathbb{R}^N$ ($\|\cdot\|_1$, $\|\cdot\|_2$, $\|\cdot\|_\infty$, $\|\cdot\|_p$); spazi di Banach
- Prodotto scalare $\langle x,y\rangle=\sum x_iy_i$; Cauchy-Schwarz $|\langle x,y\rangle|\leq\|x\|_2\|y\|_2$

### §3 Funzioni di più variabili (pp. 38-69)
- Limiti in $\mathbb{R}^N$: ε-δ, coordinate polari, limiti di restrizioni (tecnica di controesempio)
- Derivate parziali; gradiente $\nabla f$; derivabilità parziale $\not\Rightarrow$ continuità
- Differenziabilità: def. con o-piccolo di $|h|$; differenziale $df_{x_0}(h)=\langle\nabla f(x_0),h\rangle$
- Teorema del differenziale: $\partial f/\partial x_i$ continue $\Rightarrow$ differenziabile
- Piano tangente (iper-piano in $\mathbb{R}^N$); derivate direzionali $D_vf=\langle\nabla f,v\rangle$
- Regola della catena; funzioni con gradiente nullo $\to$ costanti
- Taylor al 2° ordine: $f(x)=f(x_0)+\langle\nabla f(x_0),x-x_0\rangle+\frac{1}{2}\langle D^2f(x_0)(x-x_0),x-x_0\rangle+o(\|x-x_0\|^2)$
- Matrice hessiana $D^2f$ simmetrica (Schwarz); condizione necessaria I ordine ($\nabla f=0$)
- Cond. nec. II ordine (semidefinita pos./neg. ai minimi/massimi); cond. suff. II ordine (DP/DN/indefinita)
- Ottimizzazione su compatti: Weierstrass + frontiera

### §4 Misura e integrale di Lebesgue (pp. 70-112)
- Motivazione: limiti di Riemann (funzione di Dirichlet, passaggio al limite)
- Plurintervalli, misura aperto/compatto, misura interna/esterna, insiemi misurabili
- Funzioni misurabili; integrale per funzioni non negative; sommabilità
- Proprietà: linearità, monotonia, additività; insiemi a misura nulla; quasi ovunque
- **Beppo Levi** (conv. monotona): $f_n\nearrow f$ q.o. $\Rightarrow$ $\lim\int f_n=\int f$
- **Lemma di Fatou**: $\int\liminf f_n\leq\liminf\int f_n$
- **Lebesgue** (conv. dominata): $f_n\to f$ q.o., $|f_n|\leq g$ sommabile $\Rightarrow$ $\lim\int f_n=\int f$
- Derivazione sotto segno di integrale (Feynman's trick)
- Sezioni di insiemi; **Fubini**: $\int\int f(x,y)\,dy\,dx = \int\int f(x,y)\,dx\,dy$; **Tonelli** (non neg.)
- Integrali doppi su domini normali
- Cambio di variabile: $\int_B f = \int_A f(\Phi)|\det J_\Phi|$
- Coordinate polari (Jac $=\rho$), sferiche (Jac $=\rho^2\sin\varphi$), cilindriche (Jac $=\rho$)

### §5 Spazi $L^p$ (pp. 113-117)
- $L^p(E)$ come insieme quoziente (equivalenza q.o.); norma $\|\cdot\|_{L^p}$
- Disuguaglianza di Young; esponenti coniugati $1/p+1/q=1$
- **Hölder**: $\int|fg|\leq\|f\|_{L^p}\|g\|_{L^q}$ (dim. via Young)
- **Minkowski**: $\|f+g\|_{L^p}\leq\|f\|_{L^p}+\|g\|_{L^p}$ (dim. via Hölder)
- $L^\infty$: funzioni essenzialmente limitate; $\|f\|_{L^\infty}=\inf\{K:|f|\leq K\ \text{q.o.}\}$
- Fischer-Riesz: $L^p(E)$ è di Banach $\forall p\in[1,+\infty]$

### §6 Curve e integrali curvilinei (pp. 118-130)
- Curve $\varphi:[a,b]\to\mathbb{R}^N$; sostegno; curva regolare ($C^1$, $\varphi'\neq 0$)
- Lunghezza: $L(\varphi)=\int_a^b|\varphi'(t)|\,dt$; curva rettificabile
- Integrale curvilineo di I specie: $\int_\gamma f\,ds=\int_a^b f(\varphi(t))|\varphi'(t)|\,dt$
- Forme differenziali $\omega=\sum F_i\,dx_i$; integrale di II specie: $\int_\gamma\omega=\int_a^b\langle F(\varphi(t)),\varphi'(t)\rangle\,dt$
- Differenziale $dU$; forme esatte ($\omega=dU$): $\int_\gamma dU=U(B)-U(A)$
- Condizione necessaria di esattezza ($\partial P/\partial y=\partial Q/\partial x$); su dominio s.c. è anche sufficiente

## Note di lettura

- Dispensa ricca di esempi grafici e controesempi: ogni definizione è accompagnata da figure e casi limite.
- Il §3 (funzioni di più variabili) è il nucleo del corso e il più collegato a ML (gradiente, Taylor, ottimizzazione).
- Il §4 (Lebesgue) è il passo fondamentale verso l'analisi funzionale; i 3 teoremi di convergenza sono strumenti da memorizzare.
- I $L^p$ (§5) sono il punto di arrivo: fondamentali per comprendere la teoria delle equazioni differenziali e la probabilità moderna.

## Pagine wiki create/aggiornate da questa ingest

**Create (5):**
- [[Successioni di funzioni]] — §1
- [[Calcolo differenziale in più variabili]] — §3
- [[Integrale di Lebesgue]] — §4
- [[Spazi Lp]] — §5
- [[Curve e integrali curvilinei]] — §6

**Aggiornata (1):**
- [[Spazio metrico]] — arricchita con §2 (completezza, Banach, norme, Cauchy-Schwarz)

**Corso:**
- [[Analisi Matematica II]] — 🟡→🟢

## Fonti
- `raw/appunti/analisi2.pdf`
