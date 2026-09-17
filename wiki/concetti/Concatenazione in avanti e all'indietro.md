---
tipo: concetto
titolo: Concatenazione in avanti e all'indietro
tag: [fond-ai, logica, inferenza, programmazione-logica]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Concatenazione in avanti e all'indietro

Algoritmi di deduzione automatica per basi di conoscenza composte da **[[Clausole di Horn|clausole definite]]** (al più un letterale positivo). Entrambi hanno complessità **lineare** nel numero di clausole.

## Concatenazione in avanti (Forward Chaining)

**Idea**: partire dai fatti noti e derivare nuove conclusioni finché non si raggiunge la query $q$ o non è più possibile fare inferenze.

Ogni passo applica **Modus Ponens**: se tutte le premesse di una regola sono vere, si aggiunge la conclusione ai fatti noti.

**Algoritmo PL-CA-CONSEGUE?(KB, q):**

```
conto[c] ← numero di premesse della clausola c
inferiti[s] ← false per tutti i simboli
coda ← simboli inizialmente veri nella KB (fatti)

while coda non è vuota:
  p ← POP(coda)
  if p = q: return true
  if inferiti[p] = false:
    inferiti[p] ← true
    for each clausola c in KB dove p è nella premessa:
      decrementa conto[c]
      if conto[c] = 0:
        aggiungi c.CONCLUSIONE alla coda

return false
```

**Correttezza e completezza**: l'algoritmo è corretto (deriva solo conseguenze logiche) e completo (ogni conseguenza logica della KB è derivabile).

**Interpretazione**: la concatenazione in avanti può essere vista come una **ricerca su grafo AND-OR** della KB, dove:
- I nodi AND corrispondono alle premesse di una regola (tutte devono essere vere)
- I nodi OR corrispondono a simboli derivabili da più regole

**Caratteristica**: ragionamento **guidato dai dati** (data-driven, bottom-up).

## Concatenazione all'indietro (Backward Chaining)

**Idea**: partire dalla query $q$ e risalire verso i fatti noti, cercando le regole che hanno $q$ come conclusione e verificando che le loro premesse siano dimostrabili.

**Algoritmo:**
```
se q è un fatto noto: return true
se q è già stata tentata (evitare cicli): return false
per ogni clausola c con c.CONCLUSIONE = q:
  if TUTTE le premesse di c sono dimostrabili:
    return true
return false
```

**Interpretazione**: ragionamento **guidato dall'obiettivo** (goal-driven, top-down). Analogo alla ricerca su grafo AND-OR, ma esplorata dalla radice (la query) verso le foglie (i fatti).

**Caratteristica**: non deriva tutte le conseguenze logiche della KB, ma solo quelle rilevanti alla query → più efficiente se la query è specifica.

## Confronto

| Aspetto | Concatenazione in avanti | Concatenazione all'indietro |
|---|---|---|
| Direzione | Dai fatti alla query | Dalla query ai fatti |
| Tipo di ragionamento | Guidato dai dati (bottom-up) | Guidato dall'obiettivo (top-down) |
| Quando conviene | KB con molti fatti, query non nota a priori | Query specifica, KB grande |
| Completezza | Sì | Sì (con gestione dei cicli) |

## Legame con Prolog

La concatenazione all'indietro con **unificazione** è la base del meccanismo di risoluzione di **Prolog**. Le clausole definite di Prolog corrispondono esattamente alle regole e ai fatti delle clausole di Horn.

## Grafo AND-OR

Una KB a clausole definite si può rappresentare come **grafo AND-OR**:
- Un nodo per ogni simbolo proposizionale
- Archi OR: un simbolo può essere derivato da più regole
- Archi AND: le premesse di una regola devono essere tutte vere (nodo AND figlio di tutte le premesse)

**Esempio**: se la KB contiene $A \land B \to C$, allora $C$ ha un nodo AND come figlio di $A$ e $B$.

## Complessità

Entrambi gli algoritmi sono **lineari** nel numero di clausole (per clausole proposizionali), a differenza della risoluzione generale che può essere esponenziale.

## Limitazione

Funzionano solo con **clausole definite** ([[Clausole di Horn]] con esattamente un letterale positivo), non con clausole generali.

## Estensione al primo ordine

Nella [[Logica del primo ordine]], la concatenazione in avanti/indietro usa l'**unificazione** (algoritmo di Robinson) per abbinare le premesse delle regole ai fatti della KB. Cfr. [[Logica del primo ordine]].

## Discusso in: [[Fondamenti di Intelligenza Artificiale]]

## Fonti

- [[Dispense FondAI — Galletti]] §6.5.2–6.5.3
