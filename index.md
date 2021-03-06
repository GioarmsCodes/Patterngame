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


### Mostra a schermo

La fase di mostra a schermo , inizia con la fine della fase di 
generazione, è gestita da 3 moduli : 
Mod_Round
(
1),Mod_Video control
(2)
,Mod_Lif
e
(3).
Mod_Round : è un counter un po’ modificato, che dice al 
Gestore output video quanti quadrati far vedere.
Mod_Video control : modulo che riceve in input il 
numero di quadrati da far vedere dal modulo Round 
attuale e il clock(il quale viene bloccato in determinate 
situazioni), e ha come output il quadrato(round da 
mostrare) da far vedere in quel momento , il segnale se far 
vedere a schermo e il segnale che indica la fine della 
mostra del pattern.
Il tunnel [Round da mostrare] va all’interno del 
Mod_Vide
o
(4) che codifica il numero da mostrare in output 
video per una matrice 16x16.
Mod_Lif
e : modulo che riceve un input again e da il 
commando a Mod_Video control di far rivedere l’intera
sequenza a schermo.

![image](https://user-images.githubusercontent.com/75253452/110202330-180aed80-7e68-11eb-8e94-9d452b2058e9.png)

### Controllo input

La fase di controllo dell’input, inizia con la fine della 
fase di mostra a schermo, è gestita da un modulo
:
Mod_Check
Il modulo Mod_Check(1) legge dal Mod_Memory(2) i dati che dovrà controllare.
Al click dei bottoni di input il modulo controlla se il dato 
cliccato è giusto , in caso positivo modifica l’indice di 
controllo avanti di uno, quando l’indice di controllo 
raggiungerà il numero del round attuale il modulo 
emette un segnale [prossimo] che aggiornerà il valore 
di round attuale(facendolo aumentare di 1) e questa 
modifica resetterà la parte di mostra a schermo e 
controllo input . Dunque si tornerà alla fase di mostra a 
schermo , dalla quale si ricomincerà con il valore di 
round attuale più alto.
Al raggiungimento del round scelto all’inizio della 
partita verrà messo a schermo una V in caso di vittoria 
oppure una L in caso di resa(Dopo aver cliccato again 4 
volte)
.

![image](https://user-images.githubusercontent.com/75253452/110202359-45579b80-7e68-11eb-8272-acec63cede6b.png)

