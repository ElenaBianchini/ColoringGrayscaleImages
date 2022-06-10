# ColoringGrayscaleImages

## Scopo
Lo scopo del progetto è quello di realizzare una rete neurale convoluzionale in grado di colorare automaticamente le immagini in scala di grigi. 

## Dati 
Ho utilizzato parte del dataset Places205, formato da 238.136 immagini di dimensioni 256x256. 
Nel progetto viene realizzato un train set composto da 8.000 immagini, un validation set di 2.000 immagini e un test set di 1.000 immagini. 

Tutte le immagini sono ridimensionate a 22x224 e preprocessate per ricavarne il formato LAB, a partire da quello RGB. Le immagini LAB sono composte da tre canali:
1. L: identifica la luminosità di ogni pixel attraverso un valore tra [0,100]
2. A: identifica 
3. B:

## Soluzione proposta
Il modello proprosto è caratterizzato da un'architettura di questo tipo:

> immagine

Presenta quindi:
- un **encoder** realizzato a partire dal modello della ResNet18, che viene interrotta al sesto livello. La ResNet18 è una rete per la classificazione di immagini composta da 18 livelli e connessioni residue. Viene utilizzata nel progetto per estrarre delle informazioni semantiche dalle immagini di input.
- un **decoder** realizzato da tre livelli deconvoluzionali.

L'obiettivo ultimo della rete è quello di calcolare, a partire dall'immagine in scala di grigi i canali *AB* dell'immagine, rappresentata in formato LAB. 
