# PER UN PUGNO DI BOXES
#Scafidi Roberto Antonino - Ziero Samuele - De Reggi Paolo

Progetto per il primo parziale del corso di Interactive 3D Graphics (2018/2019) con consegna entro 8/04/2019.

Team:
Scafidi Roberto Antonino - 123125,
Ziero Samuele - 107201,
De Reggi Paolo - 123783.

## Descrizione generale del progetto
Il progetto consiste in una applicazione web caratterizzata da un mini-gioco di simulazione di una trenino su rotaia. L'idea è quella di realizzare un ambiente in stile Far west, caratterizzato da pochi elementi interattivi e ulteriori elementi automatici cosi da fornire all'utente una esperienza di "visita" di un ambiente. A tal proposito abbiamo infatti costruito numerosi elementi automatici cosi da simulare una sorta di parco a tema dove si possono vedere elementi caratteristici per l'appunto del tema stesso e interagire, anche se in minima parte, con gli oggetti.

In questa app, l'esperienza parte con una splashscreen contenente le istruzioni, cosi da informare l'utente che potrà controllare il treno e il suo vagone attraverso movimenti di accelerazione e decellerazione e guardare gli effetti che questo ha nel paesaggio. L'utente avrà a disposizione i comandi "W" e "S", rispettivamente per accelerare e decellerare il treno.

Durante la simulazione sarà possibile guardare l'ambiente circostante, caratterizzato dalla presenza di elementi animali quali nuvole, mulino, bandiera ecc. In particolare, alcuni di essi si muoveranno in base all'azione del treno, gestita dall'utente (come il saluto da parte dell'omino quando il treno passa nelle sue vicinanze o il fumo dalla ciminiera quando il treno è in azione). 

Abbiamo deciso di inserire degli Orbit Controls in modo tale da consentire all'utente, data la poca interattività col sistema, di analizzare attraverso le varie inquadrature fatte con il movimento del mouse e gli zoom, di analizzare la scena e guardare il paesaggio. A tal proposito abbiamo quindi preferito non abilitare anche i comandi "freccia Su" e "freccia Giu" per i movimenti del treno, cosi da poter contemporaneamente muovere e sposare il punto di vista della camera.

### Descrizione degli elementi
**Treno:** E' costituito da 6 blocchi 3D per la motrice e 6 per il vagone. E' costituito da 2 set di ruote posizionate al di sotto dei blocchi e da 8 cubi all'interno del vagone.
**Rotaia:** E' caratterizzata da 100 traversine posizionate in modo ellittico al centro della scena. Per il posizionamento è stata una formula matematica che permette l'equo distanziamento degli elementi nell'ambiente.
**Mulino:** E' costituito da una base fissa e un blocco mobile rototraslatorio. E' posizionato al centro della scena ed è caratterizzato da 12 pale rotanti.
**Casa:** E' un elemento fisso della scena; caratterizzato da 5 blocchi, che rappresentano rispettivamente la struttura principale, il tetto, la porta e la finestra.
**Omino:** E' caratterizzato da 8 blocchi, costituendo un oggetto 3d il cui unimo movimento è quello del braccio destro.
**Bandiera:** E' costituita da 3 elementi, ed è fissa sulla posizione dell'asta.
**Arbusti:** Sono caratterizzati dall'oggetto cactus, cespuglio e albero. Nella scena vengono clonati e posizionati in modo sparso nell'ambiente
**Nuvole:** Sono caratterizzate da 12 cubi posizionati ad incastro e vengono clonate 4 volte per poi venir sospese in alto nella scena.

### Animazioni
Le animazioni principali del progetto sono state sviluppate su singole funzioni, in particolare:

**Movimento del treno+fumo:** Viene legata la motrice al vagone e posizionate secondo le leggi:
			treno.rotation.y=(angolotreno+90)*Math.PI/180;
			treno.position.set(41.5*Math.cos(angolotreno*Math.PI/180), 0, -32.5*Math.sin(angolotreno*Math.PI/180));
			vagone.rotation.y=(angolotreno-25+90)*Math.PI/180;
			vagone.position.set(41.5*Math.cos((angolotreno-25)*Math.PI/180), 0, -32.5*Math.sin((angolotreno-25)*Math.PI/180));
E' stato inoltre ovviato al problema dell'approssimazione dei floating point attraverso il controllo che ad esempio viene fatto per l'accelerazione dell'oggetto nel binario (in questa porzione di sorgente si può inoltre notare la creazione dell'animazione del fumo):
		if(accelerazioneTreno>0) {
				accelerazioneTreno=accelerazioneTreno-0.01;
				// per ovviare ai problemi con i floating point
				if(accelerazioneTreno<0.01) {
					accelerazioneTreno=0;
				}
				var altezzaFumo = Math.floor(Math.random()*3+3);
				fumo.position.set(0,altezzaFumo,0);
			}

**Movimento del mulino:** Viene effettuata una rotazione del blocco coda + pale sull'asse della struttura del mulino e inoltre vengono fatte ruotare le pale sull'asse orizzontale; nota interessante il delay applicato alla rotazione:
	var elapsed=(Date.now()-startedTime)/1000;
			if(elapsed>periodo_rotazione_blocco) {
				startedTime=Date.now();
			}

**Movimento dell'omino:** L'animazione dell'omino è caratterizzata da un range che viene applicato al braccio per non effettuare un movimento innaturale. Viene inoltre effettuata l'animazione solo nel momento in cui l'angolo del treno si avvicina e raggiunge quello dell'omino stesso; qui una porzione di codice in cui si può notare l'applicazione delle leggi orarie per limitare l'azione del braccio.
       if(angoloMod>0 && angoloMod<=30) {
					vincoloBraccio.rotation.z=(140-(140/30)*angoloMod)*Math.PI/180;
				}
				if(angoloMod>30 && angoloMod<60) {
					vincoloBraccio.rotation.z=(-(140/30)*(-angoloMod%30))*Math.PI/180;
				}

**Movimento della bandiera:** La legge oraria della bandiera viene applicata come nel caso dell'omino, per un range ristretto di movimenti. Viene riportato un esempio di accelerazione-

var accelerazione=Math.sin((360/periodo_rotazione_blocco)*elapsed*Math.PI/180);
			
**Movimento delle nuvole:** PEr quanto riguarda il movimento delle nuvole, l'animazione viene applicata a step di azione. Nell'esempio sottostante possiamo notare l'applicazione della legge a tutte le 4 porzioni di elemento.

				nuvole[0].position.y += movimento_nuvole_step;
				nuvole[1].position.y += movimento_nuvole_step;
				nuvole[2].position.y -= movimento_nuvole_step;
				nuvole[3].position.y -= movimento_nuvole_step;

				movimento_nuvole_now+=Math.abs(movimento_nuvole_step);

## Screenshots del progetto
Immagini nella loro totalità

## Processo produttivo e planning steps

Per lo sviluppo del progetto abbiamo seguito un metodo Divide et Impera in cui le fasi principali sono state:
- Progettazione e design dell'idea;
- Creazione placeholder e definizione delle idee utilizzando three.js;
- Sostituizione man mano degli elementi fittizi con le versioni finali;
- Organizzazione generale degli elementi;
- Ottimizzazione delle leggi e calcolo efficienza del codice;
- Pulizia codice e organizzazione degli elementi;
- Creazione relazione del progetto.

## Credits
Per il progetto sono state utilizzate solo texture distribuite sotto licenza Creative Commons, (in particolare tutte provenienti dal sito https://freestocktextures.com) eventualmente rielaborate per massimizzare l'efficienza nel caricamento.