---
tipo: concetto
titolo: Modello Entità-Relazione
tag: [database, er, gestione-dati, cs, progettazione]
cluster: sistemi
fonti: 1
ultima-modifica: 2026-05-06
---

# Modello Entità-Relazione

Strumento per la **progettazione concettuale** di basi di dati. Rappresenta la realtà a un livello astratto, indipendente dall'implementazione fisica o dal modello logico scelto.

## Entità e attributi

Un'**entità** è una classe di oggetti del mondo reale con esistenza autonoma (es. `Persona`, `Prodotto`). Ogni entità ha un insieme di **attributi** che la descrivono.

### Tipi di attributi

| Tipo | Descrizione | Esempio |
|---|---|---|
| **Semplice** | Valore atomico | `nome`, `età` |
| **Composto** | Strutturato in sotto-attributi | `indirizzo = (via, città, CAP)` |
| **Multi-valore** | Più valori per la stessa istanza | `telefoni = {123, 456}` |
| **Derivato** | Calcolabile da altri attributi | `età` da `data_nascita` |

## Relazioni ER

Una **relazione** (associazione) descrive un legame logico tra due o più entità. Può avere attributi propri (es. `data_inizio` in una relazione `Impiego` tra `Persona` e `Azienda`).

**Ruoli:** quando la stessa entità partecipa più volte a una relazione con funzioni diverse, si etichettano i partecipanti con ruoli. Esempio: nella relazione `Supervisione` su `Persona × Persona`, i ruoli sono `supervisore` e `supervisionato`.

## ISA (Generalizzazione/Specializzazione)

La gerarchia ISA ("is-a") esprime che un'entità $B$ è un tipo speciale di $A$: ogni istanza di $B$ è anche un'istanza di $A$.

**Proprietà della relazione ISA:**
- **Riflessiva:** $A \text{ ISA } A$.
- **Transitiva:** $B \text{ ISA } A$ e $C \text{ ISA } B$ $\Rightarrow$ $C \text{ ISA } A$.
- **Antisimmetrica:** $A \text{ ISA } B$ e $B \text{ ISA } A$ $\Rightarrow$ $A = B$.

**Generalizzazione** = partire da entità specifiche e astrarre un'entità padre.

### Tipi di generalizzazione

| Tipo | Significato |
|---|---|
| **Completa** | Ogni istanza del padre appartiene ad almeno un figlio |
| **Incompleta** | Possono esistere istanze del padre non coperte da nessun figlio |
| **Disgiunta** | Ogni istanza appartiene ad al più un figlio |
| **Sovrapposta** | Un'istanza può appartenere a più figli contemporaneamente |

## Vincoli di cardinalità

Esprimono quante istanze di un'entità possono partecipare a un'istanza di una relazione.

| Tipo | Descrizione | Esempio |
|---|---|---|
| **1:1** | Uno a uno | `Persona — Passaporto` |
| **1:N** | Uno a molti | `Dipartimento — Impiegati` |
| **M:N** | Molti a molti | `Studente — Corso` |

**Partecipazione:**
- **Totale (obbligatoria):** ogni istanza partecipa almeno una volta.
- **Parziale (opzionale):** alcune istanze possono non partecipare.

## Identificatori

Un **identificatore** distingue univocamente le istanze di un'entità.

| Tipo | Descrizione |
|---|---|
| **Interno** | Formato da attributi dell'entità stessa (analogo alla chiave primaria) |
| **Esterno** | Include attributi di entità collegate tramite relazioni (entità debole) |
| **Essenziale** | L'identificatore non può essere NULL |

**Entità debole:** entità la cui identificazione dipende da un'altra entità tramite una relazione; usa un identificatore esterno (la chiave primaria include la FK verso l'entità forte).

## Ridondanze

Una **ridondanza** è un'informazione derivabile da altri dati già presenti nel modello.

- **Intensionale:** derivabile per definizione (es. `età` derivabile da `data_nascita`).
- **Estensionale:** derivabile da percorsi nel grafo ER (es. `totale_ordine` derivabile sommando i `prezzi` dei prodotti collegati).

Le ridondanze migliorano le performance delle query ma introducono rischio di inconsistenza — vanno documentate e valutate caso per caso.

## Dal modello ER al modello relazionale

Regole principali di traduzione:

1. Ogni **entità** → tabella; l'identificatore diventa chiave primaria.
2. Ogni **relazione M:N** → tabella con chiavi primarie delle entità coinvolte + attributi propri.
3. **Relazione 1:N** → FK nella tabella del lato N che referenzia il lato 1.
4. **Relazione 1:1** → FK in una delle due tabelle (preferibilmente quella con partecipazione totale).
5. **Entità debole** → la chiave primaria include la FK verso l'entità forte.
6. **ISA** → tre strategie: (a) tabella unica con discriminatore, (b) tabella per ciascun figlio con FK al padre, (c) tabella solo per le foglie.

## Connessioni

- Modello logico risultante: [[Modello relazionale]]
- Interrogazione: [[SQL]]
- Corso: [[Gestione dei Dati]]

## Fonti

- [[Dispense GestioneDati — Galletti]] (§4, pp. 26-32)
