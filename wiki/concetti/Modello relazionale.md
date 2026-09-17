---
tipo: concetto
titolo: Modello relazionale
tag: [database, sql, gestione-dati, cs]
cluster: sistemi
fonti: 1
ultima-modifica: 2026-05-06
---

# Modello relazionale

## Struttura dei dati

Una **relazione** matematica su domini $D_1, \ldots, D_n$ è un sottoinsieme del prodotto cartesiano $D_1 \times \cdots \times D_n$. Gli elementi sono chiamati **n-uple** (o tuple).

**Schema di relazione:** $R(A_1:D_1,\ldots,A_n:D_n)$ — nome della relazione più lista di attributi con dominio. Lo schema è la struttura (intensione); l'**istanza** è il contenuto (estensione) in un dato momento.

**Schema di base di dati:** insieme di schemi di relazione $\{R_1,\ldots,R_k\}$.

## Algebra relazionale

Linguaggio formale per interrogare basi di dati relazionali. Operatori principali:

### Ridenominazione ($\rho$)

$\rho_{B \leftarrow A}(R)$: rinomina l'attributo $A$ in $B$.

### Selezione ($\sigma$)

$\sigma_\phi(R)$: restituisce le tuple di $R$ che soddisfano la condizione $\phi$.

### Proiezione ($\pi$)

$\pi_{A_1,\ldots,A_k}(R)$: mantiene solo gli attributi indicati ed **elimina i duplicati** (relazione = insieme).

### Join

**Join naturale** ($R \bowtie S$): prodotto cartesiano + selezione sulle colonne con stesso nome. Se non ci sono attributi comuni, equivale al prodotto cartesiano.

**Theta-join** ($R \bowtie_\phi S$): $\sigma_\phi(R \times S)$ — join con condizione generica.

**Equi-join:** theta-join dove $\phi$ è una congiunzione di uguaglianze.

**Self-join:** join di una relazione con se stessa (richiede ridenominazione preventiva).

**Outer join:** mantiene le tuple senza corrispondenza, completando con NULL.
- $R \leftouterjoin S$ (left), $R \rightouterjoin S$ (right), $R \fullouterjoin S$ (full).

### Operatori insiemistici

Richiedono relazioni **compatibili** (stesso schema):
- **Unione** $R \cup S$, **Intersezione** $R \cap S$, **Differenza** $R \setminus S$.

## Informazione incompleta e NULL

**NULL** rappresenta un valore sconosciuto, inesistente o non applicabile. Non è un valore del dominio.

**Mondo chiuso (CWA — Closed World Assumption):** tutto ciò che non è nella base di dati è falso. La negazione in algebra relazionale è la differenza insiemistica.

Nelle condizioni con NULL, la valutazione non è TRUE/FALSE ma può essere UNKNOWN (logica a tre valori).

## Vincoli di integrità

### Intra-relazionali (su una singola relazione)

- **Vincolo di dominio:** i valori degli attributi appartengono al dominio specificato.
- **Superchiave:** un insieme di attributi $K$ è superchiave se non esistono due tuple con gli stessi valori su $K$.
- **Chiave:** superchiave minimale (nessun sottoinsieme proprio è superchiave).
- **Chiave primaria:** chiave scelta come identificatore principale; **non ammette NULL**.

### Inter-relazionali (tra relazioni)

- **Vincolo di integrità referenziale (FK):** un attributo di $R$ referenzia la chiave primaria di $S$. Ogni valore non-NULL deve corrispondere a un valore esistente in $S$.

## Connessioni

- Linguaggio di interrogazione: [[SQL]]
- Progettazione concettuale: [[Modello Entità-Relazione]]
- Corso: [[Gestione dei Dati]]

## Fonti

- [[Dispense GestioneDati — Galletti]] (§2, pp. 2-9)
