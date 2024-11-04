Verifica di Vulnerabilità tramite Caricamento di File su DVWA con Shell PHP

Obiettivo: Testare la possibilità di sfruttare la vulnerabilità del caricamento di file nella piattaforma Damn Vulnerable Web Application (DVWA) usando una shell PHP per ottenere accesso remoto su Metasploitable da un sistema Kali Linux.

Passaggi

Conferma della Connessione tra Kali Linux e Metasploitable

 Da Kali Linux, si invia un comando di ping all’indirizzo IP di Metasploitable.
Comando usato: ping 192.168.1.129
 Tramite browser su Kali Linux, si inserisce l’indirizzo IP di Metasploitable per raggiungere DVWA (http://192.168.1.129/dvwa).
Si accede a DVWA e si imposta il livello di sicurezza su “Low” per abilitare il caricamento di file senza restrizioni.

Preparazione della Shell PHP

 Creare una shell PHP che permetta l’esecuzione di comandi remoti su Metasploitable una volta caricata.
Creazione di un file PHP chiamato shell.php contenente codice che permette l’esecuzione remota di comandi inviati tramite un parametro URL cmd.
Caricamento della Shell PHP su DVWA

 Testare se shell.php può essere caricato tramite il modulo di caricamento file di DVWA, sfruttando la vulnerabilità del sistema.
 Si seleziona e carica il file shell.php tramite la sezione di caricamento file di DVWA.
Risultato: Il caricamento ha successo, come confermato da un messaggio visibile su DVWA.
Test della Shell PHP con Burp Suite

 Utilizzare Burp Suite per intercettare e modificare le richieste HTTP alla shell PHP.
Con Burp Suite in modalità di intercettazione, si inserisce nel browser l’URL della shell caricata con l’aggiunta di ?cmd=ls per eseguire il comando ls (http://192.168.1.129/dvwa/hackable/uploads/shell.php?cmd=ls).
Burp Suite intercetta e inoltra la richiesta, e l’output del comando ls appare nella pagina web.
