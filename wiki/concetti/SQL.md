---
tipo: concetto
titolo: SQL
tag: [database, sql, gestione-dati, cs]
cluster: sistemi
fonti: 1
ultima-modifica: 2026-05-06
---

# SQL

Structured Query Language — linguaggio standard per DBMS relazionali. Si divide in quattro sottoparti:

| Sottolingua | Scopo | Comandi principali |
|---|---|---|
| **DDL** (Data Definition Language) | Definire/modificare lo schema | `CREATE`, `ALTER`, `DROP` |
| **DML** (Data Manipulation Language) | Inserire/modificare/cancellare dati | `INSERT`, `UPDATE`, `DELETE` |
| **DQL** (Data Query Language) | Interrogare i dati | `SELECT` |
| **DCL** (Data Control Language) | Gestire permessi | `GRANT`, `REVOKE` |

## SELECT — struttura e semantica

```sql
SELECT [DISTINCT] <espressioni>
FROM <tabelle/join>
[WHERE <condizione>]
[GROUP BY <attributi>]
[HAVING <condizione su gruppi>]
[ORDER BY <attributi> [ASC|DESC]]
```

**Ordine di valutazione logico:** `FROM` → `WHERE` → `GROUP BY` → `HAVING` → `SELECT` → `DISTINCT` → `ORDER BY`.

### FROM e JOIN

```sql
-- Join implicito (prodotto cartesiano + WHERE)
SELECT * FROM R, S WHERE R.A = S.A;

-- Inner join esplicito
SELECT * FROM R JOIN S ON R.A = S.A;

-- Natural join (match su colonne con stesso nome)
SELECT * FROM R NATURAL JOIN S;

-- Outer join
SELECT * FROM R LEFT OUTER JOIN S ON R.A = S.A;
SELECT * FROM R RIGHT OUTER JOIN S ON R.A = S.A;
SELECT * FROM R FULL OUTER JOIN S ON R.A = S.A;
```

### WHERE

Condizione booleana su attributi. NULL non soddisfa mai `= NULL` — si usa `IS NULL` / `IS NOT NULL`. Operatori: `=`, `<>`, `<`, `>`, `<=`, `>=`, `BETWEEN`, `IN`, `LIKE`, `AND`, `OR`, `NOT`.

### GROUP BY e aggregazioni

```sql
SELECT dipartimento, COUNT(*), AVG(stipendio)
FROM Impiegati
GROUP BY dipartimento
HAVING AVG(stipendio) > 50000;
```

Funzioni aggregate: `COUNT(*)`, `COUNT(DISTINCT A)`, `SUM(A)`, `AVG(A)`, `MIN(A)`, `MAX(A)`.

**Regola:** nella `SELECT` dopo un `GROUP BY`, si possono usare solo attributi presenti nel `GROUP BY` oppure funzioni aggregate.

**HAVING vs WHERE:** `WHERE` filtra prima del raggruppamento (sulle singole tuple); `HAVING` filtra dopo (sui gruppi aggregati).

### Operazioni insiemistiche

```sql
SELECT A FROM R
UNION [ALL]        -- ALL mantiene i duplicati
SELECT A FROM S;

SELECT A FROM R INTERSECT SELECT A FROM S;
SELECT A FROM R EXCEPT SELECT A FROM S;
```

`UNION`, `INTERSECT`, `EXCEPT` richiedono compatibilità degli schemi.

## DDL — Definizione dello schema

```sql
CREATE TABLE Impiegati (
    matricola    INTEGER       PRIMARY KEY,
    nome         VARCHAR(50)   NOT NULL,
    dipartimento VARCHAR(30)   REFERENCES Dipartimenti(nome)
                               ON DELETE SET NULL,
    stipendio    DECIMAL(10,2) DEFAULT 0.0,
    CHECK (stipendio >= 0)
);

ALTER TABLE Impiegati ADD COLUMN email VARCHAR(100);
ALTER TABLE Impiegati DROP COLUMN email;

DROP TABLE Impiegati;
```

**Vincoli:**
- `NOT NULL` — valore obbligatorio.
- `PRIMARY KEY` — chiave primaria (implica NOT NULL + UNIQUE).
- `UNIQUE` — vincolo di unicità (ammette NULL).
- `FOREIGN KEY ... REFERENCES` — integrità referenziale. Azioni possibili su cancellazione/aggiornamento: `CASCADE`, `SET NULL`, `RESTRICT`, `NO ACTION`.
- `CHECK (condizione)` — vincolo arbitrario sul dominio.
- `DEFAULT valore` — valore di default all'inserimento.

## DML — Manipolazione dei dati

```sql
-- Inserimento
INSERT INTO Impiegati (matricola, nome) VALUES (123, 'Mario');

-- Modifica
UPDATE Impiegati SET stipendio = stipendio * 1.1
WHERE dipartimento = 'IT';

-- Cancellazione
DELETE FROM Impiegati WHERE stipendio IS NULL;
```

## Subquery

### Nel WHERE

```sql
-- Subquery scalare
SELECT nome FROM Impiegati
WHERE stipendio > (SELECT AVG(stipendio) FROM Impiegati);

-- Con IN
SELECT nome FROM Impiegati
WHERE dip IN (SELECT nome FROM Dipartimenti WHERE sede = 'Roma');

-- Con EXISTS (correlata)
SELECT nome FROM Impiegati E
WHERE EXISTS (SELECT 1 FROM Progetti P WHERE P.resp = E.matricola);

-- Con ALL / ANY
SELECT nome FROM Impiegati
WHERE stipendio > ALL (SELECT stipendio FROM Impiegati WHERE dip = 'HR');
```

### Nel FROM — CTE (Common Table Expression)

```sql
WITH AvgPerDip AS (
    SELECT dipartimento, AVG(stipendio) AS media
    FROM Impiegati GROUP BY dipartimento
)
SELECT * FROM AvgPerDip WHERE media > 60000;
```

### Nella SELECT (scalare)

```sql
SELECT nome,
    (SELECT COUNT(*) FROM Progetti WHERE resp = matricola) AS n_progetti
FROM Impiegati;
```

## CASE

```sql
SELECT nome,
    CASE
        WHEN stipendio < 30000 THEN 'basso'
        WHEN stipendio < 60000 THEN 'medio'
        ELSE 'alto'
    END AS fascia
FROM Impiegati;
```

## CREATE VIEW

```sql
CREATE VIEW ImpiegatiIT AS
SELECT * FROM Impiegati WHERE dipartimento = 'IT';
```

Una vista è una query memorizzata che si comporta come una tabella virtuale. Utile per: semplificazione, sicurezza (esporre solo certi attributi/tuple), riuso. Di default non materializza i dati — ogni accesso riesegue la query sottostante.

## Connessioni

- Fondamento teorico: [[Modello relazionale]] (algebra relazionale → SQL)
- Progettazione: [[Modello Entità-Relazione]] (schema ER → schema SQL)
- Corso: [[Gestione dei Dati]]

## Fonti

- [[Dispense GestioneDati — Galletti]] (§3, pp. 10-25)
