---
tipo: concetto
titolo: Tabella hash
tag: [algoritmi, strutture-dati]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Tabella hash

Una **tabella hash** mappa chiavi a valori usando una **funzione hash** `h: U → {0, …, m-1}` che comprime lo spazio delle chiavi `U` in un array di taglia `m`.

## Tabella a indirizzamento diretto

Se le chiavi sono interi in `{0, …, u-1}`, possiamo usare un array `T[0..u-1]` con accesso O(1). Impraticabile se `u` è grande.

## Hash table

Usa `h(k)` per mappare la chiave `k` a una posizione in un array di taglia `m << u`. Le operazioni ideali (senza collisioni): **insert, search, delete** in O(1).

## Collisioni

Quando `h(k₁) = h(k₂)` per `k₁ ≠ k₂`. Strategie:

- **Chaining** (concatenamento): ogni slot contiene una lista di coppie (chiave, valore). Complessità media O(1 + α) dove `α = n/m` è il **fattore di carico**.
- **Open addressing**: si cerca il prossimo slot libero (linear probing, quadratic probing, double hashing).

## Scelta della funzione hash

Deve distribuire le chiavi uniformemente. Metodi comuni:
- **Division method**: `h(k) = k mod m` (m primo lontano da potenze di 2)
- **Multiplication method**: `h(k) = ⌊m·(k·A mod 1)⌋` con `A ∈ (0,1)`
- **Universal hashing**: classe di funzioni, scelta casuale evita worst-case per qualunque input

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §3.7-3.8, struttura dati fondamentale per ricerca O(1).
- [[Apprendimento Bayesiano]]: le tabelle hash appaiono nell'implementazione efficiente dei modelli grafici e nei sistemi di caching.

## Fonti

- [[Dispense TecProg — Galletti]] (§3.7-3.8, pp. 19-20)
