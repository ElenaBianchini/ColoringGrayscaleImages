# ColoringGrayscaleImages

## Scopo
Lo scopo del progetto è quello di realizzare una rete neurale convoluzionale in grado di colorare automaticamente le immagini in scala di grigi. 

## Soluzione proposta
Il modello proprosto è caratterizzato da un'architettura di questo tipo:

> immagine

Presenta quindi:
- un **encoder** realizzato a partire dal modello della ResNet18, che viene interrotta al sesto livello. La ResNet18 è una rete per la classificazione di immagini composta da 18 livelli e connessioni residue. Viene utilizzata nel progetto per estrarre delle informazioni semantiche dalle immagini di input.
- un **decoder** realizzato da tre livelli deconvoluzionali.

L'obiettivo ultimo della rete è quello di calcolare, a partire dall'immagine in scala di grigi i canali *AB* dell'immagine, rappresentata in formato LAB. 
