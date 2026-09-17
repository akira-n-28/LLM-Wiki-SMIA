---
tipo: concetto
titolo: Alberi di Beth
tag: [fond-ai, logica, inferenza, refutazione]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Alberi di Beth

Il **metodo di Beth** è un algoritmo di **deduzione automatica per refutazione**: per verificare che $A$ sia tautologia, si cerca un contromodello di $A$ costruendo un albero semantico. Se l'albero è chiuso, nessun contromodello esiste, quindi $A$ è tautologia.

## Principio fondamentale

$$A \text{ è tautologia} \iff A \text{ non ha contromodelli}$$

**Procedura:**
1. Supporre che esista un contromodello per $A$ (inizializzare l'albero con $\lnot A$)
2. Costruire l'albero secondo le regole semantiche
3. Se tutti i rami si chiudono → contraddizione → $A$ è tautologia
4. Se un ramo rimane aperto → controesempio estratto da quel ramo

## Costruzione dell'albero

Lo sviluppo dell'albero è guidato dalla **semantica dei connettivi**: ad ogni nodo si associa una formula (vera o falsa) e si sviluppano le sottoformule secondo le condizioni di verità.

**Regole di sviluppo** (in base al connettivo principale):

| Formula vera | Formula falsa |
|---|---|
| $\alpha \land \beta$: aggiungi $\alpha$ e $\beta$ (un figlio) | $\alpha \land \beta$: aggiungi $\alpha$ o $\beta$ (due figli) |
| $\alpha \lor \beta$: aggiungi $\alpha$ o $\beta$ (due figli) | $\alpha \lor \beta$: aggiungi $\alpha$ e $\beta$ (un figlio) |
| $\alpha \to \beta$: aggiungi $\lnot\alpha$ o $\beta$ (due figli) | $\alpha \to \beta$: aggiungi $\alpha$ e $\lnot\beta$ (un figlio) |
| $\lnot\lnot\alpha$: aggiungi $\alpha$ (un figlio) | $\lnot\lnot\alpha$: aggiungi $\lnot\alpha$ (un figlio) |
| $\lnot(\alpha \land \beta)$: equiv. $\alpha \land \beta$ falsa | $\lnot(\alpha \lor \beta)$: equiv. $\alpha \lor \beta$ falsa |

**Regola generale:**
- Connettivi $\land$, $\lnot\lor$, $\lnot\to$, $\lnot\lnot$: **un figlio** (sviluppo lineare)
- Connettivi $\lnot\land$, $\lor$, $\to$: **due figli** (biforcazione)

## Chiusura e terminazione

Un **ramo è chiuso** se contiene sia $A$ che $\lnot A$ per qualche formula $A$ (contraddizione).

- L'**albero è chiuso** se tutti i rami sono chiusi → formula di partenza è tautologia
- L'**albero è aperto** se almeno un ramo rimane aperto → da quel ramo si può estrarre un controesempio

**Teorema.** La costruzione dell'albero di Beth termina sempre in un numero finito di passi.

**Teorema.** Il metodo è **corretto** (nessun falso negativo) e **completo** (nessun falso positivo).

## Algoritmo (stadi intermedi)

**Inizializzazione**: $\tau_1$ = singolo nodo etichettato con $\lnot A$ (la negazione della formula da verificare).

**Generico passo $k$**: si esamina un ramo non chiuso di $\tau_k$:
- Se non ci sono formule sviluppabili → albero completato e **aperto** (controesempio)
- Se ci sono formule sviluppabili → si sceglie una formula e si applica la regola corrispondente per formare $\tau_{k+1}$

## Estensione al primo ordine

Gli alberi di Beth si estendono alla [[Logica del primo ordine]] con regole aggiuntive per i quantificatori:

| Formula | Sviluppo |
|---|---|
| $\forall x C$ (vera) | Si aggiunge $C[t/x]$ per ogni costante $t$ presente nel ramo |
| $\exists x C$ (vera) | Si aggiunge $C[c/x]$ per una nuova costante $c$ |
| $\lnot \forall x C$ (vera) | Come $\exists x \lnot C$ |
| $\lnot \exists x C$ (vera) | Come $\forall x \lnot C$ |

Un ramo è chiuso nella logica dei predicati quando tutte le formule sono state analizzate e tutte le istanze dei quantificatori universali sono state considerate.

**Nota:** nella logica del primo ordine l'albero può non terminare (la logica è indecidibile), ma se la formula è insoddisfacibile, l'albero terminerà.

## Estrarre un contromodello

Da un ramo aperto si legge un contromodello:
1. Dominio $D$: tutte le costanti che compaiono nel ramo
2. Predicati: $P^M = \{P(a_i) \mid P(a_i) \text{ compare nel ramo e } \lnot P(a_i) \text{ non compare}\}$

## Confronto con altri metodi

| Metodo | Approccio | Complessità |
|---|---|---|
| Model checking | Enumera tutti i modelli | $O(2^n)$ |
| Alberi di Beth | Ricerca contromodelli | Finita (LP), semi-decidibile (LPO) |
| [[Sistema Hilbertiano]] | Derivazione sintattica | — |
| [[Risoluzione (RES)]] | Refutazione su CNF | — |

## Collegamenti

- Si fonda su: [[Conseguenza logica]], [[Logica proposizionale]]
- Complementare a: [[Sistema Hilbertiano]], [[Risoluzione (RES)]]
- Discusso in: [[Fondamenti di Intelligenza Artificiale]]

## Fonti

- [[Dispense FondAI — Galletti]] §5, §7.4 (estensione al primo ordine)
