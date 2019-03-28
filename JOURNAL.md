# JOURNAL del progetto di Interactive 3d Graphics: Scafidi Roberto A. - Ziero Samuele - De Reggi Paolo

Progetto per il primo parziale del corso di Interactive 3D Graphics (2018/2019) con consegna entro 8/04/2019

Team:
Scafidi Roberto Antonino - 123125,
Ziero Samuele - 107201,
De Reggi Paolo - 123783.

## Idea generale e decisioni di design

L'idea generale del progetto è stata quella di sviluppare una scena interattiva costituita da elementi animati automaticamente ed elementi comandati dall'utente. Abbiamo pensato dunque a una scena ispirata alla cinematografia del Far West (da cui la citazione del titolo "Per un pugno di boxes" in riferimento al quasi omonimo film), costituita da un ambiente di campagna con una ferrovia, il cui treno è azionabile dall'utente attraverso i tasti W e S della tastiera. L'animazione prevede l'accelerazione e decellerazione del treno, seguita poi dai vari elementi della scena che arricchiscono l'ambiente.

## Progressi del progetto

PARTENZA:
Siamo partiti con lo sviluppo dell'idea di design attraverso il disegno grafico a mano. Siamo riusciti a coincidere le varie idee per un fine comune, costruendo un mockup su carta per poi svilupparne uno attraverso mezzi elettronici.

----inserire bozza---

PASSI DI SVILUPPO
-Abbiamo costruito dei placeholder nella scena, inserendo dei cubi neri all'interno del ground per definire gli spazi e renderci conto di come sarebbero stati posizionati i vari elementi nella scena.
-Il passo successivo è stato quello di ricolorare gli elementi cosi da renderci conto in modo preciso cosa andava fatto. In questo modo abbiamo costituito gli elementi base: Mulino, casa, treno.
- Sostituzione dei primi placeholder con oggetti 3D. Il primo passo è stato inserire l'oggetto mulino con il suo blocco di rotazione. Dopo aver studiato i moti di rotazione che avremmo voluto ottenere, sono state implementate le prime cinematiche anche se i movimenti al momento non risultano fluidi abbastanza.
-Creazione di una legge oraria per il mulino che viene predisposto di un tempo per cui si muove inizialmente accelerando verso destra per poi decellerare e continuare per il verso opposto. Viene dunque creata una rototraslazione in quanto anche le pale procedono la loro rotazione per seguire il vento.
-Ottimizzazione della funzione cinematica cosi da consentire un movimento fluido e naturale.
-Inizio di attribuzione delle texure agli elementi mulino e applicazione della texture per il ground. In questo modo è stato più semplice immaginare il proseguimento della creazione degli altri oggetti.
-Costruzione della ferrovia e quindi della traiettoria che dovrà seguire il treno. E' stato pensato attraverso la creazione di elementi "traversina" che costituiscono il supporto per la rotaia.
-Avendo quindi costruito la traiettoria per il treno è stata implementata la funzione per intercettare il pulsante da tastiera cosi da poter gestire l'aumento o la diminuzione della velocità del treno. 
-Modifica dei valori della traiettoria della ferrovia (inizialmente circolare), per l'alternativa ellittica, considerata più adatta al paesaggio-
-Costruzione della casa, della bandiera e dell'omino. 
-Costruzione della locomotiva e inserimento della legge oraria che permette al treno di muoversi all'interno della ferrovia. 

----arrivati al commit del 27 Marzo





## Scelte di implementazione


## Problemi riscontrati e soluzioni


	- design your scene on graphed paper, deriving, for each box, the necessary translation, rotation, and scaling values. Then, you can directly code the scene in three.js
	
