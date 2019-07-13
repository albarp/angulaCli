# angulaCli

uno strumento per standardizzare e semplificare la gestione di un progetto angular. Si occupa di creare componenti, servizi, etc.. ma anche di preparare la app per il rilascio e eseguire i test

# Creazione App:

*ng new --help // lista comandi di new*

*ng new my-app --d // genera la app in una cartella chiamata my-app, ma non salva*

*ng new my-app --routing // fa un modulo per i componenti e uno per il routing*

i comandi ng si possono accorpare, per esempio:

*ng new my-app -st // genera la app con inline style (s) e inline template (t). Vale solo per le opzioni corte*

# Linting
*ng lint --format stylish // lancia il lint e formatta l'output in modo che sia più leggibile*

# Componenti:

*ng g c customer // crea il componente customer. Crea anche la cartella customer a partire da src/app. Il percorso si può specificare*

--flat: niente cartella per il file del componente

--inline-template (-t): template html nel file .ts

--inline-style (-s): stile css nel file .ts

--skipTests=true|false: test sì, test no

--viewEncapsulation=Emulated|Native|None|ShadowDom: come si propagano i css? Emulated=quelli del main html arrivano fino al componente, ma no viceversa, Native=quelli del main html non arrivano al componente e quelli del componente non si propagano all'html padre, None=li stili non hanno scope

--changeDetection=Default|OnPush: il default aggiorna la grafica ad ogni cambio di valore di una variabile utilizzat dal template. Con OnPush la grafica è aggiornata solo se si modifica il riferimento aalla sorgente dati (per esempio si fa un nuovo oggetto)

--dry-run (-d): solo output, ma non creare nulla

--prefix: prefisso per i componenti

# Direttive:

ng g d search-box // crea una direttiva che mi sembra essere un componente fatto di solo codice

# Servizi:

ng g s sales-data

# Classi:

ng g cl models/customer -d // genera una classe

ng g i models/person // genera un'interfaccia

ng g e models/gender // genera un'enum

# Pipe:

ng g p shared/init-caps // genera una pipe nella cartella shared

ng g p shared/init-caps -m app.module // dice in che modulo mettere la pipe

# Moduli:

ng g m login // crea un modulo

ng g m login -m app.module // come sopra, ma importa anche il modulo appena creato nel modulo app.module

un opzione interessante è --routing che crea due moduli: uno per i componenti e uno per il routing. Ricordarsi di usarla con -m e nome del modulo principale per importare il modulo

# Guardie

*ng g guard auth*

# Build
*ng build --help* // output to /dist/[your app]

i file che produce sono:

|File|Description|
|---|---|
|runtime.js|WebPack runtime|
|main.js|App Code|
|polyfills.js|Platform polifills|
|style.s|Styles|
|vendor.js|Angular and other vendro files|

*ng build --stats-json* // mette nella cartella dist un file json con le statistiche dei pacchetti inclusi nel buil. Non usare in prod

e poi si usa un comando chiamato webpack-bundle-analyzer (da installare a parte) per analizzare il file:

*npx webpack-bundle-analyzer dist/[your app]/stats.json*

# Serve
*ng serve -o --prod* // è un'opzione per testare il sito come 

# Capabilities
*ng add <external library>* // aggiunge la external library al mio progetto
  
|Op|Description|
|-|-|
|ng add @angular/pwa|Progressive Web App|
|ng add @angular/material|Material design|
|ng add @angular/elements|Per utilizzare il componente angular come web component?|
|ng add @ng-bootstrap/schematics|template per la generazione automatica di componenti ngbootstrap??|

Una volta installate le nuove capabilities, e se sono disponibili gli schematics, si possono generare automaticamente le porzioni di codice:

*ng g @angular/material:material-nav --name nav* // crea un componente di navigazione di nome nav
*ng g @angular/material:material-dashboard --name dashboard* // una bella dashboard già pronta
*ng g @angular/material:material-table --name customer-list* // una bellissima tabella di nome customer list

# Update
Il sito di riferimento è https://update.angular.io

*ng update* // lanciato senza parametri fa vedere quali pacchetti andrebbero aggiornati

Ricordarsi dell'opzione -d per fare un dry run

# Multiple peojects:
E' possibile creare diversi sotto progetti, dopo aver fatto il progetto principale. I sotto progetti sono raccolti nella cartella *projects*. I sotto progetti, e il progetto principale, possono essere compilati separatamente e ognuno avrà la rispettiva cartella sotto *dist*
Angular.json contiene la definizione dei progetti.

*ng new home* // fa il progetto home

*ng generate application help-area* / crea il progetto help-area

I comandi della cli possono essere indirizzati ad un progetto piuttosto che ad un altro
