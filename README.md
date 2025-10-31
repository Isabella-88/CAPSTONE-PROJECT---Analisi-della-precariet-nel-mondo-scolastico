▶**INTRODUZIONE E OBIETTIVO DEL PROGETTO**

Il seguente progetto vuole analizzare l’andamento della precarietà nel sistema scolastico italiano, con particolare attenzione al personale docente. 
Ogni anno migliaia di docenti vivono una condizione di incertezza, con contratti a tempo determinato che spesso si protraggono per molti anni prima di arrivare, se mai accade, a una stabilizzazione. 

È un fenomeno che purtroppo, anziché migliorare, sta peggiorando sempre più, scoraggiando numerosi validi docenti nel perseguire la strada dell’insegnamento. Questa situazione non solo influisce sulla vita degli insegnanti, ma ha conseguenze dirette anche sugli studenti, portando una discontinuità didattica e inficiando sulla qualità del servizio scolastico.





▶**FONTI UTILIZZATE E DESCRIZIONE DEL DATASET**

Dati ufficiali del MIM (Ministero dell’Istruzione e del Merito) 

Link: https://dati.istruzione.it/opendata/opendata/catalogo/elements1/?area=Personale+Scuola&utm_source=chatgpt.com




▶**STRUMENTI UTILIZZATI**

Gli strumenti utilizzati sono stati: 

◼ Editor di Power query in Excel

◼ Python (con le librerie NumPy e Pandas)

◼ Power BI.




▶**DESCRIZIONE DEI DATI E METADATI**

Tramite le fonti open data del Ministero dell'Istruzione ho trovato, per ogni anno scolastico dal 2015 al 2023, file Excel contenenti informazioni Sui docenti a tempo indeterminato e sui docenti supplenti, per un totale di 16 file Excel.
Ogni file Excel aveva le seguenti colonne:

▪ AnnoScolastico - Anno scolastico di riferimento anagrafe scuola

▪ Provincia - Provincia di appartenenza territoriale del Comune ove è sita la scuola

▪ OrdineScuola - Indica il grado di istruzione di titolarità. Assume i valori: SCUOLA INFANZA, SCUOLA PRIMARIA, SCUOLA SECONDARIA I GRADO, SCUOLA SECONDARIA II GRADO

▪ TipoPosto - Tipo posto. Assume valori: NORMALE e SOSTEGNO

▪ TipoSupplenza - Tipologia supplenza. Assume valori: ANNUALE per le supplenze di durata fino al 31/08 e FINO AL TERMINE per le supplenze di durata fino al 30/06

▪ FasciaEta - Indica la fascia di età. Assume i seguenti valori: FINO A 34, TRA 35 E 44, TRA 45 E 54, OLTRE 54. La fascia di età è calcolata al 31 dicembre dell'anno scolastico di riferimento

▪ ContrattoFinalRuolo - Indica se il contratto è finalizzato al ruolo [SI/NO]

▪ ContrattoOrarioIntero - Indica se il contratto è su orario intero [SI/NO]

▪ DocentiSupplentiMaschi - Numero di docenti supplenti maschi. Non viene conteggiato il personale educativo e gli insegnanti di religione

▪ DocentiSupplentiFemmine - Numero di docenti supplenti femmine. Non viene conteggiato il personale educativo e gli insegnanti di religione




▶**FASE ETL: METODOLOGIA UTILIZZATA E DESCRIZIONE DEL MODELLO**

Nella prima fase di osservazione e manipolazione dei dati ho inizialmente unito, grazie all'editor di Power Query, tutti i file Excel in un unico file Excel, aggiungendo una colonna “TipologiaDocente” che distingue tra docenti indeterminati e supplenti, in modo da poter successivamente fare un confronto tra le due.
Ho anche eliminato le colonne superflue, che non erano necessarie per la mia analisi, e ho pulito in generale il mio dataset.

Successivamente, poiché avrei utilizzato Power BI per le visualizzazioni della mia analisi, ho ritenuto necessario, al fine di impostare lo star schema, utilizzare Python.

Python, grazie all’utilizzo delle sue librerie, mi ha permesso di estrapolare l'informazione riguardo le province in una tabella separata, associare poi ad ogni provincia il codice provincia, la regione di appartenenza e ad ogni regione l'area geografica (nord, centro, sud e isole). Poi all'interno della tabella principale ho sostituito la colonna provincia con la colonna codice provincia. In questo modo tutte le informazioni geografiche erano a sé stanti e mi avrebbe permesso di impostare la mia analisi in Power BI in modo più corretto e dinamico.
Tutte le altre informazioni e le ho lasciate nella tabella principale perché avrebbe avuto poco senso creare una tabella per ogni informazione.

Dopodiché ho estrapolato i miei due file Excel da Python: il file Excel principale e il file Excel con le informazioni geografiche.
Questi due file poi li ho caricati su Power BI, mettendoli in relazione tra di loro, e ho iniziato la costruzione del mio report.




▶**DESCRIZIONE DEL REPORT**

L’impostazione del progetto segue una logica di analisi progressiva: si parte da una panoramica generale sul corpo docente per poi approfondire, in pagine dedicate, le principali dimensioni di analisi: temporale, distributiva e geografica.
Ogni sezione è accompagnata da visualizzazioni interattive che consentono di esplorare i dati da diverse prospettive e individuare le tendenze principali relative alla stabilità e alla precarietà del personale scolastico.
L’obiettivo è offrire una lettura integrata e interattiva del fenomeno della precarietà nel sistema scolastico.




▶**CONCLUSIONI**

Dall’analisi dei dati emerge che, nel complesso, il numero di docenti di ruolo risulta nettamente superiore rispetto a quello dei docenti supplenti. Tuttavia, osservando l’andamento nel tempo, si nota lieve diminuzione dei docenti di ruolo e un corrispondente incremento dei supplenti, segnale di un progressivo aumento della precarietà nel sistema scolastico.

Come prevedibile, la componente femminile è largamente prevalente rispetto a quella maschile. Analizzando la distribuzione per fascia d’età, si conferma una tendenza già nota: la stabilità contrattuale si raggiunge mediamente in età avanzata. La fascia oltre i 54 anni è infatti quella con la maggiore presenza di docenti di ruolo, mentre tra i più giovani prevalgono nettamente i supplenti.

A livello territoriale, la distribuzione appare complessivamente omogenea, ma il Nord Italia concentra un numero più elevato di docenti, soprattutto di ruolo.

Infine, per quanto riguarda il grado di istruzione, la scuola secondaria di secondo grado risulta quella con il maggior numero di docenti complessivi.
