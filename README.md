# angulaCli

* uno strumento per standardizzare e semplificare la gestione di un progetto angular. Si occupa di creare componenti, servizi, etc.. ma anche di preparare la app per il rilascio e eseguire i test

Creazione App:

ng new --help // lista comandi di new

ng new my-app --d // genera la app in una cartella chiamata my-app, ma non salva

i comandi ng si possono accorpare, per esempio:

ng new my-app -st // genera la app con inline style (s) e inline template (t). Vale solo per le opzioni corte

Linting
ng lint --format stylish // lancia il lint e formatta l'output in modo che sia più leggibile

Componenti:

ng g c customer // crea il componente customer

--flat: niente cartella per il file del componente
--inline-template (-t): template html nel file .ts
--inline-style (-s): stile css nel file .ts
--skipTests=true|false: test sì, test no
--viewEncapsulation=Emulated|Native|None|ShadowDom: come si propagano i css? Emulated=quelli del main html arrivano fino al componente, ma no viceversa, Native=quelli del main html non arrivano al componente e quelli del componente non si propagano all'html padre, None=li stili non hanno scope
--changeDetection=Default|OnPush: il default aggiorna la grafica ad ogni cambio di valore di una variabile utilizzat dal template. Con OnPush la grafica è aggiornata solo se si modifica il riferimento aalla sorgente dati (per esempio si fa un nuovo oggetto)
--dry-run (-d): solo output, ma non creare nulla
