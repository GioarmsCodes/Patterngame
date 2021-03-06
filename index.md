## Welcome to Pattern Memory Game site


### In cosa consiste il progetto?

Il mio progetto consiste nel simulare il gioco del pattern memory su logisim

### Come si gioca?

Bisogna innanzitutto scegliere quanti round si vuole giocare e avviare la simulazione del clock(8Hz di frequenza per una giocabilità ideale).

aspettare che si completi il caricamento della barra di caricamento: 
![image](https://user-images.githubusercontent.com/75253452/110202157-29072f00-7e67-11eb-8ee4-e23e2c168192.png)


In seguito al quale seguirà una combinazione di quadrati(3) che dovranno essere indovinati dall’utente tramite gli
appositi bottoni.
In caso di inserimento corretto dei quadrati si passa al round successivo dove il numero dei quadrati aumenterà di 1. 
Questo processo continuerà fino al raggiungimento del round desiderato, al completamento del quale si vincerà.
L’utente avrà a disposizione un tasto again per rivedere la combinazione ,questo tasto potrà essere cliccato solo 3 
volte, in seguito del quale il tasto avrà la funzione di bottone di resa.


![image](https://user-images.githubusercontent.com/75253452/110202193-5a7ffa80-7e67-11eb-9572-d68e5db37781.png)


### Scelte progettuali
## • Il Progetto è suddiviso in 3 parti :
# • Generazione pattern
# • Mostra a schermo
# • Controllo Input


### Generazione pattern
La generazione del pattern è gestita dal modulo 
Mod_Generazione
(
1), il quale emetterà un segnale g 
fine alla fine della generazione.
Il clock passerà al Mod_Rando
m
(2) e al 
Mod_Index
(3) per tutta la durata della generazione, 
in seguito della quale verrà bloccato grazie al 
segnale g fine.
Mod_Random : modulo che per ogni passaggio di 
clock genera un numero random su 4 bit.(il 
quadrato che l’utente dovrà indovinare
)
Mod_Index : modulo che ha la funzione di un 
counter e dice al circuito in quale indice
(indirizzo) 
salvare il numero generato
.
Il numero generato e l’indice andranno all’interno 
del Mod_Memory (4 )dove il numero random 
generato verrà salvato all’indirizzo dell’indice.

![image](https://user-images.githubusercontent.com/75253452/110202280-cbbfad80-7e67-11eb-9012-d4a1e77f1035.png)

