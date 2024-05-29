# AXE DOCTOR

AxeDoctor è un dispositivo (hardware) di monitoraggio del software ESP-Miner di skot
(https://github.com/skot/ESP-Miner).

Il progetto utilizza la scheda di sviluppo display LCD da 1,9 pollici LILYGO T-Display-S3 ESP32-S3 
con funzionalità Wi-Fi e Bluetooth integrate. La scheda è dotata di un microprocessore dual-core LX7, 
16 MB di memoria flash, 8 MB di PSRAM e funziona con un alimentatore da 3,3 V.

# Caratteristiche principali:

* Monitoraggio fino a 6 dispositivi basati su ESP-Miner (bitaxe, luckyminer,...);
* I parametri di lavoro monitorati sono:
	1) Temperatura
	2) Voltage
	3) Velocità della ventola
	4) Hashrate
	5) Shared accepted
	6) Shared rejected
	7) Uptime
	8) Best difficulty
* Interfaccia grafica semplice ed intuitiva:
	1) Pannello sintetico mediante icone verde/rosso
	2) Pannello con i parametri di lavoro
	3) Pannello con i problemi rilevati
	4) Screen saver (matrix)
	5) Spegnimento automatico del display
* Sistema di rilevamento degli IP dei dispositivi da monitorare:
	1) Automatico
	2) Fisso
* Interfaccia WIFI di configurazione:
	1) IP dispositivi
	2) Parametri di funzionamento
	3) Email
	4) Licenza d'uso
* Invio di email:
	1) Configurazione degli IP e parametri di funzionamento
	2) Report periodico dello stato di funzionamento dei dispositivi monitorati
	3) Lista dei problemi rilevati dal monitoraggio
* Reboot automatico dei dispositivi bloccati:
	1) Quando hashrate basso
* Versione iniziale dimostrativa:
	1) Funziona fino a 4 ore
	2) Funziona solo 5 volte
* Aggiornamento alla versione pienamente funzionante (senza limitazioni di tempo e accensioni):
	1) Acquistando una regolare licenza


# Preparazione

1) Recuperare i seguenti file:
	
	1) 0x0000_AxeDoctor_Bootloader_V1.bin
	2) 0x8000_AxeDoctor_Partitions_V1.bin
	3) 0x10000_AxeDoctor_Firmware_V1.bin
	
2) Andare su https://espressif.github.io/esptool-js/

3) Collegare l'AxeDoctor al PC e metterlo nella modalità di aggiornamento:
	1) Collegare USB al PC
	2) Tenere premuto il tasto BOOT e premere il tasto RESET
	3) Rilasciare il tasto RESET
	4) Il display deve restare spento
4) Andare su "Program", selezionare Baudrate "115200" e cliccare su CONNECT
5) Selezionare/Aggiungere i file del punto precedente indicando l'indirizzo di memoria corrispondente
6) Cliccare su Program
5) Cliccare su DISCONNECT
6) Premere sul tasto laterale di RESET


# Configurazione

1) Accendere l'AxeDoctor e posizionarlo vicino allo stesso router su cui sono collegati tutti i
   dispositivi ESP-Miner da monitorare
2) Accedere alla pagina di configurazione tramite il WIFI collegandosi al AP chiamato "AxeDoctor_XXXXXXXX"
3) Premere sul tasto "WIFI config"
4) Compilare la form:

	1) Campo AXEIP1/6: Inserire un IP fisso (ex. 192.168.0.100) di un dispositivo ESP-Miner, oppure
		 AXEIP1: Inserire il codice "RESCAN" per attivare la modalità automatica di scansione degli IP
			 tutte le volte che si accende l'AxeDoctor
		 AXEIP1: Inserire il codice "AUTO" per eseguire una scansione solo la prima volta e registrare
			 gli IP trovati come fissi alla prossima accensione del AxeDoctor
		 AXEIP2: (sprimentale) inserire un indirizzo IP (ex. 192.168.0.100) da utilizzare come riferimento su cui
			 applicare la modalità "RESCAN"

		 ACTIVATION KEY: inserire il codice della licenza

		 Inserire i parametri di funzionamento desiderati:
		 	Refresh minutes: Inserire ogni quanti minuti viene eseguito il monitoraggio di tutti i
					 dispositivi ESP-Miner configurati
			Check voltage  : Inserire 1=SI, 0=NO se si vuole abilitare il monitoraggio della tensione
					 di alimentazione dei dispositivi ESP-Miner configurati
			Max temperature: Inserire la soglia massima della temperatura (C)

		 SMTP Server / Email Port / Email User / Email Password : inserire la configurazione di una email

5) Premere SALVA e attendere il riavvio del AxeDoctor
6) AxeDoctor si collegherà automaticamente al WIFI configurato precedentemente
   ATTENZIONE: è molto importante che in questa fase l'AxeDoctor riconosca il vostro router WIFI
   (compare in alto sopra utente/password, eventualmente fare refresh)


# Tasti

1) Durante il normale funzionamento
	1) Tasto SOPRA: premere una volta per interrompere la pausa, due per riprendere la verifica dei dispositivi ESP-Miner
	2) Tasto SOTTO: premere più volte per accendere e spegnere il display
	3) Insieme: Reset di fabbrica (format)

2) Durante la scansione degli IP
	1) Insieme: Reset della configurazione WIFI

3) Quando la licenza è scaduta
	1) Insieme: Reset di fabbrica (format)

4) Tasto laterale: RESET

# Raccomandazioni e casi di uso

AxeDoctor è indicato nei seguenti casi di uso:
	1) Tutti i dispositivi ESP-Minier sono nella stessa sottorete del AxeDoctor
	2) Tutti i dispositivi ESP-Miner sono sempre accesi H24:
		2A) Potete usare la configurazione FISSA degli IP se li conoscete;
		    solitamente anche se spegnete un dispositivo il vostro router
		    assegnerà possibilmente sempre lo stesso indirizzo IP.
		2B) Potete usare la configurazione automatica degli IP (RESCAN), ogni volta
		    che accenderete il vostro AxeDoctor inpiegherà circa 20 minuti
		    per scandagliare tutta la sua sottorete alla ricerca di 
		    dispositivi ESP-Miner (esempio 192.168.0.X con X>1)
 		    In questi casi potete anche accendere il vostro AxeDoctor in fasce orarie
		    affinchè ogni volta venga eseguita nuovamente una scansione degli IP
		2C) Potete usare la configurazione automatica degli IP solo la prima volta (AUTO),
  		    verrà eseguita una RESCAN solo una volta il cui risultato sarà
		    memorizzato come IP fissi
	3) Tutti i dispositivi ESP-Miner si accendono solo in certe fasce orarie
	   del giorno per mezzo di interruttori smart (ad esempio per sfruttare il
	   vostro impianto fotovoltaico):
		3A) In questi casi è meglio utilizzare sempre la configurazione
		    automatica degli IP (RESCAN) e il vostro AxeDoctor si dovrà accendere
		    insieme ai vostri dispositivi ESP-Miner. La funzione di scansione
		    automatica degli IP inpegherà circa 20 minuti utili per consentire
		    ai dispositivi di avviarsi regolarmente.


# Licenza
Shareware 

# Registrazione 
Prossimamente

# Hardware
https://a.aliexpress.com/_Ew7XsML https://a.aliexpress.com/_EJlkuTp

# Assistenza
axedoctorb10@gmail.com
