---
tipo: concetto
titolo: Residual Connection
tag: [reti-neurali, deep-learning, computer-vision, ottimizzazione]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# Residual Connection (Skip Connection)

Tecnica introdotta da He et al. (2015) in **ResNet** per addestrare reti neurali estremamente profonde senza incorrere nel **degradation problem**.

## Problema: Degradation

Aggiungere layer a una CNN plain peggiora le prestazioni — sia sul training che sul test set. Non è overfitting (l'errore di training aumenta). Il problema è che l'ottimizzazione diventa troppo difficile: reti più profonde non riescono nemmeno ad apprendere la funzione identità apprezzata dai layer "in più".

## Soluzione: Residual Learning

Invece di far apprendere a un blocco la trasformazione target $H(x)$, gli si fa apprendere solo il **residuo** $F(x) = H(x) - x$:

$$y = x + F(x, \phi)$$

dove $x$ è l'input che "salta" il blocco tramite la skip connection e viene sommato all'output.

Se i layer aggiuntivi non sono utili, è più facile imparare $F(x) \approx 0$ (identity mapping) che imparare $H(x) = x$ direttamente.

## Propagazione del gradiente

Durante il backpropagation, il gradiente può fluire **direttamente** attraverso la skip connection senza passare per le trasformazioni $F$:

$$\frac{\partial L}{\partial x} = \frac{\partial L}{\partial y} \cdot \frac{\partial y}{\partial x} = \frac{\partial L}{\partial y} \cdot (1 + \frac{\partial F}{\partial x})$$

Il termine "+1" garantisce che il gradiente non scompaia esponenzialmente, mitigando il **vanishing gradient** (stesso problema risolto dalle [[LSTM]] nelle RNN).

## Loss Surface

Con skip connections la loss surface diventa molto più **smooth** (liscia): minimo ben definito, senza irregolarità. Senza skip connections: picchi, valli strette, minimi locali → ottimizzazione instabile.

## Interpretazione come Ensemble

La struttura residuale crea implicitamente un **ensemble** di sottoreti di diversa profondità. La varianza dell'ensemble è ridotta rispetto a un'unica rete profonda.

## Formulazione ricorsiva

Per una sequenza di blocchi residuali:
$$h_1 = x + f_1[x, \phi_1], \quad h_2 = h_1 + f_2[h_1, \phi_2], \quad \ldots$$

Espandendo, l'output contiene sempre l'input originale $x$ più correzioni residuali successive.

## Varianti di blocco residuale

- **(a) Base:** un solo layer lineare + ReLU. L'output può avere solo valori $\geq 0$.
- **(b) Con layer lineare finale:** due layer + ReLU intermedia. Gestisce valori negativi.
- **(c) Pre-activation:** ReLU prima dei layer lineari. Meglio per reti molto profonde.

## ResNet

**Residual Network** vince ILSVRC 2015, dimostrando che si possono addestrare reti fino a 152 layer.

Struttura modulare:
- **Stem:** Conv $7 \times 7$, stride 2 + Max Pooling. Input $224 \times 224 \times 3$ → $56 \times 56 \times 64$.
- **Stage 1–4:** 4 gruppi di blocchi residuali con canali crescenti (64 → 128 → 256 → 512). Ogni stage dimezza la risoluzione e raddoppia i canali.
- **Head:** Global Average Pooling + FC + Softmax su 1000 classi.

### Bottleneck Block (ResNet-50+)

Per ridurre il costo computazionale nelle varianti profonde:

$$\text{Conv } 1 \times 1 \to \text{Conv } 3 \times 3 \to \text{Conv } 1 \times 1$$

La prima $1 \times 1$ riduce i canali (bottleneck), la $3 \times 3$ opera su meno canali, l'ultima $1 \times 1$ li espande. Ogni conv è preceduta da Batch Normalization e ReLU.

### Configurazioni standard

| Variante | Blocchi | Parametri |
|---|---|---|
| ResNet-18/34 | Base | 11M/21M |
| ResNet-50 | Bottleneck | 25M |
| ResNet-101/152 | Bottleneck | 44M/60M |

## Residual Connections fuori dalla Computer Vision

- **[[Transformer]]:** ogni sotto-strato usa `LayerNorm(x + Sublayer(x))`. Stessa idea.
- **[[LSTM]]:** il cell state si aggiorna tramite somme → gradiente highway. Motivazione analoga.
- **U-Net:** le skip connections concatenano (non sommano) feature map dell'encoder al decoder — semantica diversa ma ispirazione comune.

## Connessione con Dropout

AlexNet ha usato [[Dropout]] per le reti profonde (2012). ResNet ha dimostrato che con residual connections il dropout diventa meno necessario (le reti sono già più facili da ottimizzare). Nelle architetture moderne si usano entrambi.

## Connessione con Gradient Boosting

Concettualmente il residual learning è simile al [[Gradient Boosting]]: ogni modello nuovo apprende il residuo lasciato dal precedente. La differenza è che in ResNet tutti i blocchi si addestrano simultaneamente.

## Connessione con la Regolarizzazione

La loss surface liscia ha un effetto implicito di regolarizzazione: il modello è più robusto a piccole perturbazioni nei parametri e generalizza meglio.

## Collegamenti

- Applicato in: [[Convolutional Neural Network]], [[Transformer]]
- Motivazione: vanishing gradient (cfr. [[Recurrent Neural Network]], [[LSTM]])
- Concettualmente simile: [[Gradient Boosting]]
- Discusso in: [[Informatica per il Machine Learning]] (§14.6, pp. 64-66)

## Fonti

- [[Dispense InfML — Galletti]] (§14.6, pp. 64-66)
