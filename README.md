🛡️ Windows Security Monitoring Lab

Un progetto pratico di analisi dei log Windows e Sysmon per attività da SOC Analyst



📌 Panoramica del progetto

Questo laboratorio ha l’obiettivo di simulare attività di monitoraggio e analisi degli eventi di sicurezza generati da Windows e Sysmon.

Il progetto riproduce scenari reali che un SOC Analyst deve saper riconoscere, investigare e documentare.



Gli eventi analizzati includono:



Tentativi di accesso falliti (ID 4625)



Accessi riusciti (ID 4624)



Creazione di processi sospetti tramite PowerShell (Sysmon ID 1)



Connessioni di rete generate da PowerShell (Sysmon ID 3)



Il laboratorio è stato eseguito su Windows 10 con Sysmon correttamente installato e configurato.



🎯 Obiettivi del laboratorio

Comprendere il funzionamento dei log di sicurezza Windows.



Analizzare eventi critici relativi all’autenticazione.



Identificare processi sospetti tramite Sysmon.



Riconoscere connessioni di rete anomale generate da PowerShell.



Documentare un caso di analisi in stile SOC Analyst.



🏗️ Architettura del laboratorio

Sistema operativo: Windows 10



Strumenti utilizzati:



Visualizzatore Eventi (Event Viewer)



Sysmon v14+



PowerShell



Attività simulate:



Tentativi di login falliti e riusciti



Esecuzione di PowerShell encoded



Connessione HTTP tramite PowerShell



🔐 1. Eventi di Logon Windows

🔸 Evento 4625 — Accesso fallito

Questo evento indica un tentativo di autenticazione non riuscito.

È utile per identificare brute-force, password guessing o tentativi sospetti.



📷 Screenshot:  



!\[4625](/screenshots/logon/Screenshot 2026-05-08 183758.png)



🔸 Evento 4624 — Accesso riuscito

Indica un login completato con successo.

È fondamentale per ricostruire la timeline di un potenziale incidente.



📷 Screenshot:  



!\[4624](/screenshots/logon/Screenshot 2026-05-08 183834.png)



⚙️ 2. Eventi Sysmon

🔸 Sysmon ID 1 — Process Create (PowerShell encoded)

Sysmon registra la creazione di un processo.

In questo caso, è stato eseguito un comando PowerShell encoded:



powershell -enc SQBFAFgA



Questo comportamento è tipico di script offuscati o attività sospette.



📷 Screenshot:  



!\[Sysmon ID 1](/screenshots/sysmon/Screenshot 2026-05-08 184318.png)



🔸 Sysmon ID 3 — Network Connection Detected

Sysmon registra una connessione di rete generata da PowerShell, simulata tramite:





curl http://example.com



Questo permette di identificare eventuali comunicazioni verso host esterni.



📷 Screenshot:  



!\[Sysmon ID 3](/screenshots/sysmon/Screenshot 2026-05-08 184208.png)





🧩 MITRE ATT\&CK Mapping

Evento	Tecnica MITRE	Descrizione

PowerShell encoded	T1059.001 – PowerShell	Uso di PowerShell per eseguire comandi potenzialmente malevoli

Process Create	T1106 – Execution	Creazione di processi sospetti

Network Connection	T1041 – Exfiltration Over C2 Channel	Connessioni verso host esterni

Logon Failure	T1110 – Brute Force	Tentativi di accesso non autorizzati





🕒 Timeline dell’attività simulata



18:34 — Tentativo di accesso fallito (4625)



18:34 — Accesso riuscito (4624)



18:40 — Esecuzione PowerShell encoded (Sysmon ID 1)



18:44 — Connessione HTTP tramite PowerShell (Sysmon ID 3)



🔍 Conclusioni



Questo laboratorio dimostra come un SOC Analyst possa:



Identificare attività sospette tramite i log di Windows e Sysmon



Ricostruire una timeline di potenziali incidenti



Collegare gli eventi alle tecniche MITRE ATT\&CK



Documentare un caso reale in modo professionale



Il progetto rappresenta una base solida per chi vuole iniziare nel mondo del Blue Team e dell’Incident Detection.



📁 Struttura del repository



windows-security-monitoring-lab/

│

├── screenshots/

│   ├── logon/

│   │   ├── 4625.png

│   │   └── 4624.png

│   └── sysmon/

│       ├── sysmon\_id1\_process\_create.png

│       └── sysmon\_id3\_network\_connection.png

│

└── README.md

🙌 Autore

Progetto realizzato da Joele Bernardi, come esercizio pratico di analisi dei log e monitoraggio di sicurezza Windows.

