## activeMQ
Installazione e configurazione di base di activeMQ

scaricare il sorgente da:
```
http://activemq.apache.org/activemq-5150-release.html
```
Navigare fino alla directory bin (nel caso di macOS /macosx/bin) e lanciare:
```
./activemq start
```
Aprire un browser e digitare: 
```
http://localhost:8161/admin
````
Le credenziali di default che vengono richieste sono admin/admin.<br>
Creare una nuova coda Queues > Create (la coda viene creata anche automaticamente al running del progetto mule).<br>
Su Anypoint Studio usare il connettore JMS Publisher nel caso si voglia aggiungere alla coda, e JMS Listener nel caso si voglia leggere dalla coda.<br>
Nelle configurazioni del connettore:
```
Destination type: QUEUE
Destination: <nome coda creata>
Creare una connector configuration:
Connection > Username : admin
Connection > Password : admin
Connection Factory > Factory configuration : edit inline
Connection Factory > Broker url : tcp://localhost:61616
```
Tasto destro sul progetto: Build Path > Add External Archives e selezionare “activemq-all-5.15.0.jar” dall’archivio scaricato dal sito di ActiveMQ.<br>
Test connection deve andare a buon fine.<br>
Inviando un payload alla coda si vedrà il “Number Of Pending Messages” che viene incrementato.<br>

In ambienti di produzione normalmente viene installato in una terza macchina che serve le code.<br>
