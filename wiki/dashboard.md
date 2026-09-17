---
tipo: dashboard
titolo: Dashboard
ultima-modifica: 2026-05-06
---

# 📊 Dashboard della wiki

Pagina viva: i blocchi qui sotto si aggiornano automaticamente a ogni modifica. Richiede plugin **Dataview** abilitato (Settings → Community plugins → Dataview).

> Se vedi solo il codice grezzo invece delle tabelle, il plugin non è attivo. Vai in Settings → Community Plugins → Dataview → Enable.

---

## Sintesi globale

Distribuzione per tipo di pagina:

```dataview
TABLE WITHOUT ID
  tipo AS "Tipo",
  length(rows) AS "Pagine"
FROM "wiki"
WHERE tipo
GROUP BY tipo
SORT length(rows) DESC
```

---

## Distribuzione per cluster

Concetti + argomenti raggruppati per cluster (i colori del grafo):

```dataview
TABLE WITHOUT ID
  cluster AS "Cluster",
  length(rows) AS "Pagine"
FROM "wiki/concetti" OR "wiki/argomenti"
WHERE cluster
GROUP BY cluster
SORT length(rows) DESC
```

---

## Corsi (live)

Tutti i 18 corsi con docente e A.A.:

```dataview
TABLE WITHOUT ID
  file.link AS "Corso",
  docente AS "Docente",
  anno-accademico AS "A.A."
FROM "wiki/corsi"
SORT file.name ASC
```

---

## Fonti per data ingest (più recenti in alto)

```dataview
TABLE WITHOUT ID
  file.link AS "Fonte",
  corso AS "Corso",
  data-ingest AS "Ingest",
  pagine AS "PDF pp."
FROM "wiki/fonti"
SORT data-ingest DESC
```

---

## Concetti modificati di recente

Le ultime 20 pagine concetto su cui si è lavorato:

```dataview
TABLE WITHOUT ID
  file.link AS "Concetto",
  cluster AS "Cluster",
  ultima-modifica AS "Modificato"
FROM "wiki/concetti"
SORT ultima-modifica DESC
LIMIT 20
```

---

## Pagine orfane (nessun link entrante)

Concetti che nessuno cita: candidate per integrazione o cancellazione:

```dataview
LIST
FROM "wiki/concetti"
WHERE length(file.inlinks) = 0
SORT file.name
```

---

## Argomenti trasversali

Gli 8 argomenti che attraversano più corsi:

```dataview
TABLE WITHOUT ID
  file.link AS "Argomento",
  corsi AS "Corsi attraversati"
FROM "wiki/argomenti"
WHERE tipo = "argomento"
SORT file.name
```

---

## Persone più citate

Top 15 personaggi storici per numero di citazioni nella wiki:

```dataview
TABLE WITHOUT ID
  file.link AS "Persona",
  length(file.inlinks) AS "Citazioni"
FROM "wiki/persone"
SORT length(file.inlinks) DESC
LIMIT 15
```

---

## Concetti più connessi (hub)

I 15 concetti con più link entranti — i nodi centrali della wiki:

```dataview
TABLE WITHOUT ID
  file.link AS "Concetto",
  cluster,
  length(file.inlinks) AS "Citazioni"
FROM "wiki/concetti"
SORT length(file.inlinks) DESC
LIMIT 15
```

---

## Concetti per cluster (esempio: ML)

Tutti i concetti del cluster `ml`. Cambia il valore in `WHERE` per esplorare altri cluster (`probabilistica`, `algoritmi`, `algebra`, `ottimizzazione`, `analisi`, `fisica`, `numerico`, `sistemi`, `trasversale`):

```dataview
TABLE WITHOUT ID
  file.link AS "Concetto"
FROM "wiki/concetti"
WHERE cluster = "ml"
SORT file.name
```

---

## Pagine multi-fonte

Concetti che hanno integrato più di una fonte (concetti "ricchi", arricchiti da ingest multipli):

```dataview
TABLE WITHOUT ID
  file.link AS "Concetto",
  cluster,
  fonti AS "N. fonti"
FROM "wiki/concetti"
WHERE fonti >= 2
SORT fonti DESC
```

---

## Coverage per corso

Per ciascun corso, conta quante volte è citato nei concetti (proxy: ricchezza dell'ecosistema concettuale):

```dataview
TABLE WITHOUT ID
  file.link AS "Corso",
  length(file.inlinks) AS "Citazioni in"
FROM "wiki/corsi"
SORT length(file.inlinks) DESC
```

---

## Tag più usati

Top 20 tag della wiki:

```dataviewjs
const tags = {};
const pages = dv.pages('"wiki/concetti" or "wiki/argomenti"');
for (const p of pages) {
  if (p.tag) {
    for (const t of p.tag) tags[t] = (tags[t] || 0) + 1;
  }
}
const sorted = Object.entries(tags).sort((a,b) => b[1] - a[1]).slice(0, 20);
dv.table(["Tag", "Conta"], sorted);
```

---

## Gap aperti del lint

Concetti citati ma senza pagina propria (richiedono nuova fonte):

- `[[Apprendimento non supervisionato]]` — 2 citazioni in MatML

*(Lista mantenuta a mano — Dataview non rileva link rotti senza plugin aggiuntivo.)*
