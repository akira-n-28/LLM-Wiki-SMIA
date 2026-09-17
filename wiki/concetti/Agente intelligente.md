---
tipo: concetto
titolo: Agente intelligente
tag: [fond-ai, agenti, intelligenza-artificiale]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Agente intelligente

Un agente è un sistema che percepisce l'ambiente tramite sensori e agisce su di esso tramite attuatori.

## Definizione formale

La **funzione agente** è la formulazione astratta del comportamento:

$$f: H \to A$$

dove $H$ è l'insieme delle sequenze percettive (storico completo) e $A$ è l'insieme delle azioni possibili. Il **programma agente** è un'implementazione finita della funzione agente: prende in input solo la percezione corrente, non l'intera sequenza.

## Componenti di un agente

- **Percezione**: dati rilevati dai sensori in ogni istante
- **Rappresentazione della conoscenza**: modello interno degli stati dell'ambiente
- **Ragionamento**: elaborazione della percezione per produrre una decisione razionale
- **Azione**: modifica dello stato dell'agente e dell'ambiente tramite attuatori

## Razionalità (schema PEAS)

Un agente è **razionale** se, per ogni possibile sequenza percettiva, sceglie l'azione che massimizza il valore atteso della misura della performance, sulla base di:

| Lettera | Significato |
|---|---|
| **P**erformance | Misura di prestazione da massimizzare |
| **E**nvironment | Ambiente in cui opera |
| **A**ctuators | Attuatori disponibili |
| **S**ensors | Sensori disponibili |

La razionalità richiede anche **esplorazione** (raccogliere nuove percezioni), **apprendimento** (aggiornare la conoscenza) e **autonomia** (compensare conoscenza parziale o errata).

## Classificazione degli ambienti

| Dimensione | Valori |
|---|---|
| Osservabilità | completamente / parzialmente / non osservabile |
| Agenti | unico / multi-agente |
| Determinismo | deterministico / stocastico |
| Temporalità | episodico / sequenziale |
| Dinamicità | statico / dinamico |
| Discretizzazione | discreto / continuo |

## Tipi di agenti

**Agenti reattivi semplici**: scelgono l'azione in base alla sola percezione corrente; basati su regole condizione-azione `if condizione then azione`. Limitati in ambienti parzialmente osservabili.

**Agenti reattivi basati su modello**: mantengono uno **stato interno** che tiene traccia dell'ambiente non osservabile e dell'effetto delle proprie azioni.

**Agenti basati su obiettivi**: incorporano uno o più obiettivi e usano ricerca/pianificazione per trovare la sequenza di azioni che li raggiunga. La conoscenza è modificabile dinamicamente, ma computazionalmente costosa.

**Agenti basati su utilità**: risolvono conflitti tra obiettivi con una **funzione di utilità** che assegna un valore a ogni stato. Si massimizza l'utilità attesa.

**Agenti con apprendimento**: modificano la propria funzione agente in base all'esperienza.

## Rappresentazioni dello stato

| Tipo | Descrizione | Esempio |
|---|---|---|
| **Atomica** | Ogni stato è indivisibile, scatola nera | Ricerca su grafi |
| **Fattorizzata** | Stato = vettore di variabili con valori | Variabili booleane, reali |
| **Strutturata** | Stato = relazioni tra oggetti | DB relazionali, LPO |

## Agenti PS vs agenti KB

**Agenti risolutori di problemi (PS)**: usano rappresentazione atomica; formulano il problema come ricerca nello spazio degli stati. Incapaci di fare deduzioni su informazioni non direttamente codificate. Paradigma: Formulazione → Ricerca → Esecuzione.

**Agenti basati su conoscenza (KB)**: mantengono una **base di conoscenza** (insieme di formule) e un **sistema di inferenza** per derivare nuove asserzioni. Operano tramite TELL (aggiunge formule) e ASK (interroga la KB). Costruibili in modo dichiarativo (comunicando la KB) o procedurale (codificando i comportamenti).

## Definizione formale di problema di ricerca

Dato uno spazio degli stati $S$, uno stato iniziale $S_i$, stati finali $\{S_f^0, \ldots\}$, azioni $A$, modello di transizione $\text{RESULT}: S \times A \to S$ e funzione di costo $\text{COST\_ACTION}: S \times A \times S \to \mathbb{R}$.

Una **soluzione ottima** è il cammino di costo minimo dallo stato iniziale a uno stato finale.

## Valutazione degli algoritmi di ricerca

- **Completezza**: trova sempre una soluzione se esiste
- **Ottimalità**: trova la soluzione di costo minimo
- **Complessità temporale** e **spaziale**

## Limiti degli agenti PS

Operano con rappresentazioni atomiche, quindi non possono fare deduzioni su informazioni che non siano direttamente codificate nello stato. Questo motiva il passaggio agli agenti KB e alla logica come linguaggio di rappresentazione.

## Collegamenti

- Prerequisito di: [[Ricerca A*]], [[Logica proposizionale]]
- Approfondisce: [[Logica del primo ordine]] (rappresentazione strutturata)
- Discusso in: [[Fondamenti di Intelligenza Artificiale]]

## Fonti

- [[Dispense FondAI — Galletti]] §1
