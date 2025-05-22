# Linux_Backup_home
Creare uno script che faccia il backup della /home e salvarlo dentro una cartella creata chiamata /backup dentro la cartella /opt il backup deve essere fatto giornalmente alle 04:00 e non devono esserci piu di 7 file 
# backup_home.sh

## Descrizione

Questo script bash automatizza il backup di una cartella specifica in un archivio compresso `.tar.gz` all'interno della directory di destinazione. Il backup viene eseguito solo se la data odierna rientra in un intervallo di date predefinito (1 settimana).

## Funzionamento

1. **Controllo della data:**  
   Lo script verifica che la data corrente sia compresa tra una data di inizio (`START_DATE`) e una data di fine (`END_DATE`). Se la data odierna non rientra nell'intervallo, lo script termina senza eseguire alcuna operazione.

2. **Backup:**  
   Se la data è valida, viene creato un archivio compresso (`tar.gz`) della cartella sorgente e salvato nella directory di destinazione. Il nome del file di backup include la data corrente per facilitarne l'identificazione.

## Variabili principali

- `START_DATE`: Data di inizio validità backup (formato YYYY-MM-DD)
- `END_DATE`: Data di fine validità backup (formato YYYY-MM-DD)
- `SOURCE`: Cartella da cui effettuare il backup
- `DESTINATION`: Cartella di destinazione del backup
- `BACKUP_NAME`: Nome del file di backup generato

## Esempio di utilizzo

Lo script può essere eseguito manualmente oppure schedulato tramite `cron` (su sistemi Linux) per lanciare il backup automaticamente nei giorni desiderati.

## Requisiti

- Sistema operativo Linux
- Permessi di scrittura nella cartella di destinazione (`/opt/backup`)
- Comando `tar` disponibile

## Note

Assicurarsi che i percorsi delle cartelle (`SOURCE` e `DESTINATION`) siano corretti e accessibili dallo script.

# Impostare il CRON su Linux

Per eseguire automaticamente lo script di backup nei giorni desiderati, puoi utilizzare il servizio `cron` su sistemi Linux.

1. Apri il file crontab dell'utente con il comando:

`crontab -e`

2. Aggiungi una nuova riga al file per specificare il comando dello script di backup e il tempo di esecuzione. Aggiungi la seguente riga:

`* * * * * /your/script/path/NAMEFILE`

Sostituendo `* * * * *` con l'orario di esecuzione desiderato (secondi, minuti, ore, giorno del mese, mese).

Esempio: `0 0 * * 1` eseguirà lo script alle 00:00 ogni lunedì.

3. Assiurati che il file sia eseguibile con i permessi appropriati:

`chmod +x /your/script/path/NAMEFILE`

4. Salva il file crontab e chiudi l'editor.

#### [Link per settare il crontab in modo intuitivo](https://crontab.cronhub.io/)
