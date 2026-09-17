---
tipo: fonte
titolo: Dispense AnalisiI — Galletti
autori: [Marco Galletti]
docente-corso: Luca Martinazzi
anno-accademico: 2024/2025
data-ingest: 2026-05-06
file-raw: raw/appunti/analisi-matematica-I.pdf
pagine: 163
ultima-modifica: 2026-05-06
tag: [matematica, analisi]
---

# Dispense di Analisi Matematica I — Galletti

**Riferimento file raw:** `raw/appunti/analisi-matematica-I.pdf`
**Corso:** [[Analisi Matematica I]] (prof. Luca Martinazzi, A.A. 2024/2025, SMIA Sapienza)
**Autore appunti:** [[Galletti, Marco]]

## Riassunto in 5 punti

1. **Fondamenti e topologia**: insiemi, reali, valore assoluto, sup/inf, funzioni elementari (composizione, inversa, trig e inverse), topologia di ℝ (intorni, punti di accumulazione, aperto/chiuso/compatto).
2. **Limiti e o-piccoli**: definizione topologica + ε-δ, algebra dei limiti, squeeze theorem, limiti notevoli (sin x/x, (1+1/n)^n → e), o-piccoli con 7 proprietà, espansioni asintotiche, gerarchia degli infiniti.
3. **Successioni e serie**: convergenza, Bolzano-Weierstrass (dim. bisezione), serie geometrica e armonica generalizzata (Σ1/k^α converge ↔ α>1), criteri (confronto, rapporto, Leibniz), convergenza assoluta.
4. **Differenziazione**: rapporto incrementale, derivate fondamentali, regole (Leibniz, catena, inversa), Fermat/Rolle/Lagrange (con dimostrazioni), monotonia/convessità, studio di funzione, polinomio di Taylor con resti di Peano e Lagrange.
5. **Integrazione**: integrale di Riemann (somme di Darboux), TFC I/II, tecniche (per parti, sostituzione, frazioni parziali), integrali impropri, criterio integrale di Cauchy (serie↔integrali), breve intro alle ODE.

## Argomenti trattati

### §1 Nozioni Preliminari (pp. 2-28)
- Teoria degli insiemi, logica matematica
- Numeri reali: valore assoluto, estremo superiore/inferiore, principio di Archimede
- Funzioni: grafico, composizione, inversa, pari/dispari, monotona, periodica
- Funzioni trigonometriche e inverse (arcsin, arccos, arctan)
- Topologia di ℝ: intorni, punti di accumulazione, aperto/chiuso/compatto

### §2 Limiti (pp. 29-59)
- Definizione topologica e ε-δ; unicità; limite da destra/sinistra
- Algebra dei limiti; permanenza del segno; confronto; squeeze theorem
- Limiti notevoli (6 principali); forme indeterminate; cambio di variabile
- O-piccoli: 7 proprietà; espansioni asintotiche di $e^x$, $\sin x$, $\cos x$, $\ln(1+x)$, $(1+x)^\alpha$
- Gerarchia degli infiniti: $\log x \ll x^\alpha \ll a^x \ll x!$

### §3 Successioni (pp. 60-87)
- Convergenza, divergenza; successioni monotone
- Sottosuccessioni; teorema di Bolzano-Weierstrass (dim. per bisezione)
- Prova $(1+1/n)^n \to e$ via binomio di Newton
- Serie: somme parziali; geometrica; condizione necessaria ($a_k \to 0$)
- Serie armonica generalizzata; criteri di confronto, rapporto, Leibniz
- Convergenza assoluta: $\sum|a_k|<+\infty \Rightarrow \sum a_k$ converge

### §4 Funzioni continue (pp. 88-97)
- Continuità in un punto: def. topologica + ε-δ; equivalenza al limite
- Operazioni su funzioni continue; funzioni elementari continue
- Teorema di Weierstrass (dim. via successione minimizzante + BW)
- Teorema dei valori intermedi/Bolzano (dim. per bisezione)
- Continuità uniforme; teorema di Heine-Cantor

### §5 Calcolo Differenziale (pp. 98-134)
- Rapporto incrementale; derivata come limite; approssimazione affine
- Tabella derivate fondamentali (15 formule); Leibniz, catena, inversa
- Classi $C^0, C^1, C^n, C^\infty$
- Fermat (necessità di f'=0 all'estremo interno)
- Rolle (dim.); Lagrange MVT con dim. via Rolle; corollari (monotonia)
- Convessità: $f'' \geq 0 \Leftrightarrow$ convessa; test punti critici
- Studio di funzione: asintoti orizzontali/obliqui/verticali
- Polinomio di Taylor $T^n_{f;x_0}$; unicità; resto di Peano; resto di Lagrange (via Cauchy)

### §6 Integrali (pp. 135-153)
- Partizioni, somme di Darboux $S^-, S^+$; criterio di Riemann
- Classi integrabili ($C^0$, monotone); proprietà (linearità, monotonia, additività)
- TFC II: $F(x)=\int_a^x f \Rightarrow F'=f$
- TFC I (Torricelli-Barrow): $\int_a^b f = F(b)-F(a)$
- Integrazione per parti; sostituzione; frazioni parziali per funzioni razionali
- Teorema del valor medio per integrali
- Integrali impropri (4 casi); criterio del confronto
- Criterio integrale di Cauchy (bridge serie↔integrali)

### §7 ODE — Introduzione (pp. 154-163)
- Problema di Cauchy come applicazione del calcolo integrale
- Equazioni separabili; introduzione al teorema di Cauchy-Lipschitz
- *(Trattazione completa in [[Dispense MMFI — Galletti]])*

## Note di lettura

- Dispensa molto didattica: ogni teorema ha dim. e almeno un esempio applicato.
- Il §2 (limiti, ~30 pp.) è il più denso e copre molte tecniche non ovvie.
- I polinomi di Taylor (§5.4) sono fondamentali per [[Matematica per il Machine Learning]]: l'approssimazione lineare è la base della discesa del gradiente.
- L'integrale (§6) ha connessioni forti con [[Metodi Numerici]] (quadratura) e [[Processi Stocastici]] (integrali stochastici).

## Pagine wiki aggiornate da questa ingest

**Skeleton (2026-05-04):**
- [[Analisi Matematica I]] — corso creato con programma.

**Ingest profondo (2026-05-06):**
- [[Limite di una funzione]] — creata (§2)
- [[Limiti notevoli]] — creata (§2)
- [[Successioni]] — creata (§3)
- [[Continuità di una funzione]] — creata (§4)
- [[Derivata]] — creata (§5)
- [[Polinomi di Taylor]] — creata (§5.4)
- [[Integrale di Riemann]] — creata (§6)
- [[Equazione differenziale ordinaria]] — aggiornata: aggiunta seconda fonte (§7)
- [[Analisi Matematica I]] — aggiornata: 🟡→🟢

## Fonti
- `raw/appunti/analisi-matematica-I.pdf`
