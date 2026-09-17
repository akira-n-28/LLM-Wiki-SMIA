---
tipo: fonte
titolo: Dispense GestioneDati — Galletti
autori: [Marco Galletti]
docente-corso: Antonella Poggi
anno-accademico: 2024/2025
data-ingest: 2026-05-06
file-raw: raw/appunti/gestione_dati.pdf
pagine: 32
ultima-modifica: 2026-05-06
tag: [database, sql, cs]
---

# Dispense di Gestione dei Dati — Galletti

**Riferimento file raw:** `raw/appunti/gestione_dati.pdf`
**Corso:** [[Gestione dei Dati]] (prof.ssa Antonella Poggi, A.A. 2024/2025, SMIA Sapienza)
**Autore appunti:** [[Galletti, Marco]]

## Riassunto in 5 punti

1. **DBMS e architettura:** un DBMS gestisce grandi quantità di dati persistenti e condivisi garantendo efficienza, affidabilità e indipendenza dei dati. L'architettura a 3 livelli (presentazione / logico / fisico) separa cosa è memorizzato da come è memorizzato.
2. **Modello relazionale:** i dati sono rappresentati come relazioni (tabelle) su cui operano gli operatori dell'algebra relazionale — selezione, proiezione, join (naturale, theta, outer), ridenominazione e operatori insiemistici. NULL e CWA gestiscono l'informazione incompleta.
3. **Vincoli di integrità:** superchiave (unicità), chiave primaria (unicità + NOT NULL), integrità referenziale (FK). Distinguere vincoli intra-relazionali da inter-relazionali.
4. **SQL:** DDL per definire lo schema (CREATE/ALTER/DROP TABLE, vincoli PRIMARY KEY/FK/UNIQUE/CHECK/DEFAULT), DML per modificare i dati (INSERT/UPDATE/DELETE), DQL per interrogare (SELECT con JOIN, GROUP BY, HAVING, subquery nel WHERE/FROM/SELECT, CASE, VIEW).
5. **Modello ER:** strumento di progettazione concettuale. Entità, attributi (semplici/composti/multi-valore), relazioni ER con vincoli di cardinalità (1:1, 1:N, M:N), ISA (generalizzazione completa/incompleta), identificatori (interni/esterni), ridondanze. Traduzione ER → relazionale.

## Argomenti trattati

### §1 Introduzione (pp. 1-2)
- Definizione di DBMS; proprietà: grandi quantità di dati, persistenza, condivisione
- Architettura a 3 livelli: livello di presentazione, livello logico, livello fisico (dati)
- Indipendenza dei dati: logica (cambiamento schema logico senza modificare applicazioni) e fisica

### §2 Modello relazionale (pp. 2-9)
- Relazione come sottoinsieme di $D_1 \times \cdots \times D_n$; n-uple, schema, istanza
- **Algebra relazionale:** ridenominazione $\rho$, selezione $\sigma$, proiezione $\pi$, prodotto cartesiano
- Join: naturale $\bowtie$, theta-join, equi-join, self-join
- Operatori insiemistici: unione $\cup$, intersezione $\cap$, differenza $\setminus$ (su relazioni compatibili)
- NULL e informazione incompleta; logica a tre valori
- **Mondo chiuso (CWA):** tutto ciò che non è nella BD è falso
- **Outer join:** left, right, full — tuple senza corrispondenza completate con NULL
- **Vincoli di integrità intra-relazionali:** dominio, superchiave, chiave minimale, chiave primaria (NO NULL)
- **Vincoli inter-relazionali:** integrità referenziale (FK); azioni ON DELETE/UPDATE

### §3 SQL (pp. 10-25)
- Struttura DDL/DML/DQL/DCL
- **SELECT semantica:** ordine logico FROM → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY
- JOIN: implicito (FROM R, S WHERE ...), ON, NATURAL, OUTER (LEFT/RIGHT/FULL)
- **Aggregazioni:** `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`; `HAVING` vs `WHERE`
- Operazioni insiemistiche: `UNION [ALL]`, `INTERSECT`, `EXCEPT`
- **DDL:** `CREATE TABLE` con vincoli (`NOT NULL`, `PRIMARY KEY`, `UNIQUE`, `FOREIGN KEY ... REFERENCES`, `CHECK`, `DEFAULT`); `ALTER TABLE`; `DROP TABLE`
- **DML:** `INSERT INTO ... VALUES`; `UPDATE ... SET ... WHERE`; `DELETE FROM ... WHERE`
- **Subquery:** nel `WHERE` (scalare, `IN`, `EXISTS`, `ALL`/`ANY`); nel `FROM` con CTE (`WITH`); nella `SELECT` (scalare correlata)
- **CASE WHEN ... THEN ... ELSE ... END**
- **CREATE VIEW:** vista come query memorizzata, non materializzata di default

### §4 Progettazione concettuale — Modello ER (pp. 26-32)
- Entità e attributi: semplici, composti, multi-valore, derivati
- Relazioni ER; attributi di relazione; ruoli
- **ISA:** riflessiva, transitiva, antisimmetrica; generalizzazione completa/incompleta, disgiunta/sovrapposta
- **Vincoli di cardinalità:** 1:1, 1:N, M:N; partecipazione totale/parziale
- **Identificatori:** interni (attributi), esterni (tramite relazioni — entità debole), essenziali
- **Ridondanze:** intensionali (derivabili per definizione) vs estensionali (derivabili da percorsi ER)
- Traduzione ER → relazionale: entità, relazioni M:N, FK per 1:N e 1:1, strategie ISA

## Note di lettura

- Le dispense sono compatte (32 pp.) e molto dense sul §3 (SQL, 15 pp.): è il nucleo pratico del corso.
- Il §2 (algebra relazionale) è il fondamento teorico di SQL — capire l'algebra aiuta a scrivere query corrette ed efficienti.
- Il §4 (ER) è breve ma fondamentale per la progettazione: le scelte qui si propagano su tutto lo schema SQL.

## Pagine wiki create/aggiornate da questa ingest

**Create (3):**
- [[Modello relazionale]] — §2
- [[SQL]] — §3
- [[Modello Entità-Relazione]] — §4

**Corso:**
- [[Gestione dei Dati]] — 🟡→🟢

## Fonti
- `raw/appunti/gestione_dati.pdf`
