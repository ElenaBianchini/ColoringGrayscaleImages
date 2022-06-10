# ColoringGrayscaleImages

## Scopo
Lo scopo del progetto è quello di realizzare una rete neurale convoluzionale in grado di colorare automaticamente le immagini in scala di grigi. 

## Soluzione proposta
Il modello proprosto è caratterizzato da un'architettura di questo tipo:

> immagine

Presenta quindi:
- un **encoder** realizzato a partire dal modello della ResNet18, una rete per la classificazione di immagini composta da 18 livelli e connessioni residue. Questa viene interrotta al sesto livello.
- un **decoder** realizzato da tre livelli deconvoluzionali. 

