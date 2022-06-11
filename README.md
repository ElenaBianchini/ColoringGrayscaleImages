# ColoringGrayscaleImages

## Scopo
Lo scopo del progetto è quello di realizzare una rete neurale convoluzionale in grado di colorare automaticamente le immagini in scala di grigi. 

## Dati
Viene utilizzato parte del dataset Places205, formato da 238.136 immagini di dimensioni 256x256.
Nel progetto, il train set è composto da 8.000 immagini, il validation set da 2.000 immagini e il test set da 1.000 immagini. 

Tutte le immagini sono ridimensionate a 224x224 e preprocessate per ricavarne il formato LAB, a partire da quello RGB. Le immagini in spazio di colore LAB sono composte da tre canali:
L: identifica la luminosità di ogni pixel attraverso un valore tra [0,100]
A: identifica se il colore del pixel tende al verde (valori negativi) o al rosso (valori positivi), attraverso il range [-128,127]
B: identifica se il colore del pixel tende al blu (valori negativi) o al giallo (valori positivi), attraverso il range [-128,127]

![alt text](https://github.com/ElenaBianchini/ColoringGrayscaleImages/blob/main/imgs/spazio%20di%20colore.jpg) 

## Soluzione proposta
Il modello proprosto è caratterizzato da un'architettura di questo tipo:

![alt text](https://github.com/ElenaBianchini/ColoringGrayscaleImages/blob/main/imgs/model.jpg)

Presenta quindi:
- un **encoder** realizzato a partire dal modello della ResNet18, che viene interrotta al sesto livello. La ResNet18 è una rete per la classificazione di immagini composta da 18 livelli e connessioni residue. Viene utilizzata nel progetto per estrarre delle informazioni semantiche dalle immagini di input.
- un **decoder** realizzato da tre livelli deconvoluzionali.

L'obiettivo ultimo della rete è quello di calcolare, a partire dall'immagine in scala di grigi, i canali *AB* dell'immagine, rappresentata in spazio di colore LAB. 

Viene allora usato l'*errore quadratico medio* come funzione di costo, confrontando il valore predetto con quello reale.
![alt text](https://github.com/ElenaBianchini/ColoringGrayscaleImages/blob/main/imgs/MSE.png)

Infine viene ottimizzata la funzione di costo attraverso l'ottimizzatore *Adam*, con un learning rate di 10<sup>-5</sup>.

## Allenamento
La rete è stata allenata per un totale di 6 epoche. 

Andando a tracciare l'andamento della funzione di costo durante tutto il tempo di allenamento, attraverso il software **Weights & Biases**, si ottiene un grafico di questo tipo:
![alt text](https://github.com/ElenaBianchini/ColoringGrayscaleImages/blob/main/imgs/Graficowandb.png)

Se però si vanno a studiare i valori medi dei costi durante la fase di allenamento presenti sul codice, si può notare che questi sono in leggera decrescita. Sarebbe un buon esperimento quello di provare ad aumentare le epoche di allenamento per vedere se le immagini restituite rispecchierebbero maggiormente quelle reali.

## Risultati ottenuti
La seguente rappresenta un esempio di immagine ricolorata attraverso la rete allenata:

![alt text](https://github.com/ElenaBianchini/ColoringGrayscaleImages/blob/main/imgs/esempio.png)


