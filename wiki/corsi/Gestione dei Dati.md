---
tipo: corso
titolo: Gestione dei Dati
docente: Antonella Poggi
anno-accademico: 2024/2025
codice-breve: gestione_dati
ultima-modifica: 2026-05-06
tag: [database, sql, cs, smia]
---

# Gestione dei Dati

Corso di **Gestione dei Dati** tenuto dalla prof.ssa **Antonella Poggi** nell'A.A. 2024/2025, SMIA, Sapienza. Dispense redatte da [[Galletti, Marco]] (32 pp.).

## Programma

### §1 Introduzione (pp. 1-2)
- DBMS — definizione, motivazioni; proprietà: grandi quantità di dati, persistenza, condivisione
- Architettura a 3 livelli: presentazione / logico / fisico
- Indipendenza logica e fisica dei dati

### §2 Modello relazionale (pp. 2-9)
- [[Modello relazionale]] — relazione come sottoinsieme di $D_1 \times \cdots \times D_n$; schema e istanza
- Algebra relazionale: ridenominazione $\rho$, selezione $\sigma$, proiezione $\pi$
- Join: naturale, theta, equi, self; outer join (left/right/full)
- Operatori insiemistici ($\cup$, $\cap$, $\setminus$) su relazioni compatibili
- NULL, logica a tre valori, mondo chiuso (CWA)
- Vincoli di integrità: superchiave, chiave primaria, integrità referenziale (FK)

### §3 SQL (pp. 10-25)
- [[SQL]] — DDL / DML / DQL / DCL
- SELECT: semantica (FROM→WHERE→GROUP BY→HAVING→SELECT→ORDER BY); JOIN; aggregazioni
- `UNION [ALL]`, `INTERSECT`, `EXCEPT`
- DDL: `CREATE TABLE` con vincoli; `ALTER TABLE`; `DROP TABLE`
- DML: `INSERT`, `UPDATE`, `DELETE`
- Subquery: nel `WHERE` (scalare, `IN`, `EXISTS`, `ALL`/`ANY`); nel `FROM` (CTE `WITH`); nella `SELECT`
- `CASE`; `CREATE VIEW`

### §4 Progettazione concettuale (pp. 26-32)
- [[Modello Entità-Relazione]] — entità, attributi (semplici/composti/multi-valore), relazioni ER
- Ruoli; ISA (generalizzazione completa/incompleta, disgiunta/sovrapposta)
- Vincoli di cardinalità (1:1, 1:N, M:N); partecipazione totale/parziale
- Identificatori interni, esterni, essenziali; entità deboli
- Ridondanze (intensionali vs estensionali)
- Traduzione ER → relazionale

## Concetti centrali

| Concetto | Sezione | Importanza |
|---|---|---|
| [[Modello relazionale]] | §2 | fondamenta teoriche dei DB relazionali |
| [[SQL]] | §3 | linguaggio pratico per DDL/DML/DQL |
| [[Modello Entità-Relazione]] | §4 | progettazione concettuale dello schema |

## Fonti del corso

- [[Dispense GestioneDati — Galletti]] — dispense principali, 32 pp. (ingest profondo 2026-05-06)

## Stato della wiki per questo corso

🟢 **Completo** — ingest profondo effettuato (2026-05-06). 3 concetti creati.

## Connessioni trasversali con altri corsi

| Concetto GestioneDati | Corso collegato |
|---|---|
| Algebra relazionale, logica | [[Fondamenti di Intelligenza Artificiale]] (logica del primo ordine) |
| SQL, query processing | [[Informatica per il Machine Learning]] (feature engineering, dati strutturati) |
| Modello relazionale | [[Strutture Algebriche]] (relazioni, prodotto cartesiano) |
