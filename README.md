# ColoringGrayscaleImages

## Scopo
Lo scopo del progetto è quello di realizzare una rete neurale convoluzionale in grado di colorare automaticamente le immagini in scala di grigi. 

## Dati 
Viene utilizzato parte del dataset Places205, formato da 238<sup>.</<sup>136 immagini di dimensioni 256x256. 
Nel progetto il train set è composto da 8<sup>.</<sup>000 immagini, il validation set da 2<sup>.</<sup>000 immagini e il test set da 1<sup>.</<sup>000 immagini. 

Tutte le immagini sono ridimensionate a 22x224 e preprocessate per ricavarne il formato LAB, a partire da quello RGB. Le immagini in spazio di colore LAB sono composte da tre canali:
1. L: identifica la luminosità di ogni pixel attraverso un valore tra [0,100]
2. A: identifica se il colore del pixel tende al verde (valori negativi) o al rosso (valori positivi), attraverso il range [-128,127]
3. B: identifica se il colore del pixel tende al blu (valori negativi) o al giallo (valori positivi), attraverso il range [-128,127]

> immagine spazio di colore

## Soluzione proposta
Il modello proprosto è caratterizzato da un'architettura di questo tipo:

> immagine

Presenta quindi:
- un **encoder** realizzato a partire dal modello della ResNet18, che viene interrotta al sesto livello. La ResNet18 è una rete per la classificazione di immagini composta da 18 livelli e connessioni residue. Viene utilizzata nel progetto per estrarre delle informazioni semantiche dalle immagini di input.
- un **decoder** realizzato da tre livelli deconvoluzionali.

L'obiettivo ultimo della rete è quello di calcolare, a partire dall'immagine in scala di grigi, i canali *AB* dell'immagine, rappresentata in spazio di colore LAB. 

Viene allora usato l'errore quadratico medio come funzione di costo, confrontando il valore predetto con quello reale.
> immagine della formula MSE 

Infine viene ottimizzata la funzione di costo attraverso l'ottimizzatore Adam, con un learning rate di 10<sup>-5</sup>.



