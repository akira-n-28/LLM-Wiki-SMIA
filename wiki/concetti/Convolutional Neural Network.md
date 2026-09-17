---
tipo: concetto
titolo: Convolutional Neural Network
tag: [reti-neurali, deep-learning, computer-vision]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# Convolutional Neural Network (CNN)

Architettura neurale progettata per dati ad alta dimensionalità con struttura spaziale (immagini, sequenze). Sfrutta **parameter sharing** e **connessioni locali** per ridurre drasticamente il numero di parametri rispetto agli MLP fully-connected.

## Motivazioni (Inductive Bias)

Le CNN assumono che i dati abbiano queste proprietà strutturali:
- **Self-similarity:** pattern ripetuti nel dominio.
- **Translation Invariance:** il riconoscimento non dipende dalla posizione dell'oggetto.
- **Deformation Invariance:** robustezza a variazioni locali.
- **Hierarchy and Compositionality:** pixel → bordi → forme → oggetti.

Gli MLP non sfruttano queste proprietà: per un'immagine $224 \times 224 \times 3$ il numero di parametri esplode.

## Operazione di Convoluzione

**Definizione continua:** $(f \star g)(x) = \int_{-\pi}^{\pi} f(t) g(x-t) \, dt$

**Discreta 1D:** $(x * w)_i = \sum_{k=0}^{n-1} w_{i-k \bmod n} \, x_k$

**Discreta 2D** (immagini): $(f \star g)[m, n] = \sum_k \sum_\ell f[k, \ell] \, g[m-k, n-\ell]$

Il kernel scorre sull'input ("finestra mobile"); il prodotto elemento per elemento e la somma producono la **feature map**.

## Iperparametri

- **Kernel Size $K$:** dimensione spaziale del filtro.
- **Stride $S$:** passo di scorrimento. $S > 1$ riduce la dimensione dell'output (downsampling).
- **Padding $P$:** *Valid* (no padding, output $N-K+1$); *Same* (zero-padding, output = input).
- **Dilation:** "buchi" nel kernel per espandere il campo recettivo senza aumentare i parametri.

Formula dimensione output: $H_\text{out} = \left\lfloor \frac{H_\text{in} + 2P - D(K-1) - 1}{S} + 1 \right\rfloor$

## Canali e 3D

Con $C_\text{in}$ canali in input, ogni filtro è un tensore $C_\text{in} \times K \times K$ (o $C_\text{in} \times K$ in 1D). Con $C_\text{out}$ filtri, il tensore dei pesi totale è $C_\text{out} \times C_\text{in} \times K \times K$. Ogni filtro produce una feature map 2D; le $C_\text{out}$ mappe vengono impilate.

## Convoluzione $1 \times 1$

Opera solo lungo la profondità (non considera vicini spaziali). Usata per: modificare il numero di canali; aggiungere non-linearità; combinare informazioni tra canali con costo computazionale ridotto.

## Pooling (Downsampling)

Riduce progressivamente le dimensioni spaziali e dà invarianza a piccole traslazioni:
- **Max Pooling:** seleziona il massimo nella finestra. Più diffuso.
- **Average Pooling:** media dei valori.

## Struttura tipica di una ConvNet

```
Conv → ReLU → Pooling → (ripeti) → Flatten → MLP → Softmax
```

I layer iniziali estraggono feature di basso livello (bordi); i layer profondi feature ad alto livello (forme, oggetti). Il **receptive field** cresce andando in profondità.

## Architetture storiche

### AlexNet (2012)

Prima CNN profonda a vincere ImageNet (ILSVRC 2012). 8 layer totali (5 conv + 3 FC), ~60M parametri. Innovazioni principali:
- **ReLU** $f(x) = \max(0, x)$: convergenza molto più veloce di tanh/sigmoide.
- **[[Dropout]]:** nei layer FC con probabilità 0.5.
- **Data Augmentation:** traslazioni, riflessioni, crop casuali.
- **GPU Training:** parallelizzato su due GPU.
- **Local Response Normalization (LRN):** normalizzazione laterale (oggi sostituita da Batch Norm).

Input: $224 \times 224$. Output: distribuzione su 1000 classi.

### VGGNet (2014)

Standardizza il design delle CNN profonde con un principio uniforme: **solo filtri $3 \times 3$**, stride 1, padding 1 — ma in profondità crescente.

Intuizione chiave: due layer $3 \times 3$ hanno lo stesso campo recettivo effettivo di un singolo $5 \times 5$, ma con meno parametri ($2 \cdot 3^2 = 18$ vs $1 \cdot 5^2 = 25$) e più non-linearità. VGG-16: 13 conv + 3 FC, ~138M parametri. Il downsampling è delegato esclusivamente al Max Pooling.

### YOLO (Object Detection)

A differenza della classification (un'etichetta per immagine), l'object detection localizza oggetti con **bounding box**. YOLO (*You Only Look Once*) processa l'intera immagine in un unico forward pass. Input $448 \times 448$; 24 layer conv + 2 FC; output: coordinate + classi.

### Semantic Segmentation

Assegna un'etichetta semantica a **ogni pixel**. Richiede architetture encoder-decoder (cfr. [[Seq2Seq e Encoder-Decoder]]).

**Hourglass Network:** encoder (VGG-like) → bottleneck (2 FC da 4096) → decoder (Max Unpooling + Transposed Conv). Tutta l'informazione passa dal bottleneck.

**U-Net:** encoder-decoder con **skip connections laterali** (concatenazione): preserva dettagli spaziali fini non possibili col solo bottleneck. Progettata per segmentazione biomedica con dataset piccoli. Fully convolutional (nessun FC). La differenza rispetto a ResNet: le skip connections in U-Net **concatenano** le feature map (non le sommano).

## Degradation Problem e Residual Connections

Aggiungere più layer a una CNN plain (senza skip connections) peggiora le prestazioni sia sul training che sul test set (non è overfitting). Soluzione: [[Residual Connection]].

## Connessione con i Transformer

I Vision Transformer (ViT) suddividono l'immagine in patch e le trattano come token, applicando poi il [[Transformer]]. Dimostrano che l'inductive bias delle CNN non è sempre necessario con abbastanza dati.

## Loss Function per Segmentazione

Pixel-wise cross-entropy: ogni pixel è un problema di classificazione su $C$ classi.

$$L = -\frac{1}{N} \sum_{p=1}^N \sum_{c=1}^C y_{p,c} \log(\hat{y}_{p,c})$$

## Collegamenti

- Innovazioni chiave: [[Dropout]], [[Residual Connection]]
- Architettura seq: [[Seq2Seq e Encoder-Decoder]] (per segmentazione)
- Sostituisce per NLP: [[Transformer]]
- Discusso in: [[Informatica per il Machine Learning]] (§14, pp. 56-68)

## Fonti

- [[Dispense InfML — Galletti]] (§14, pp. 56-68)
