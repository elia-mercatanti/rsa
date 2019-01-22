Implementazione di algoritmi per crittografia a chiave pubblica - RSA

Implementazione di vari algoritmi per la crittografia a chiave pubblica, in particolare: Algoritmo di Euclide esteso,
Algoritmo di esponenziazione modulare veloce, Test di Miller-Rabin, Algoritmo per la generazione di numeri primi,
Schema RSA, con e senza ottimizzazione CRT.

Esercizio di programmazione 3.1 per il Corso Data Security and Privacy - Set 3

# Come Utilizzarlo

Il codice sviluppato per questo programma non richiede particolari pacchetti.
Per testare il codice è sufficente avviare tramite un interprete python il file RSA.py

# Come Funziona

Una volta avviato, il programma stampa a video un piccolo menù dove vengono indicate le nove possibili funzioni che
l'utente può eseguire. L'utente può eseguire una funzione semplicemete inserendo nella console il numero relativo alla
funzione scelta. Di seguito viene riportata una breve descrizione delle nove funzioni e cosa richiedono in input.

1. Extended Euclidean Algorithm.
   Funzione che consente di eseguire l'algoritmo esteso di euclide su due numeri interi restituendo l'MCD tra i due
   numeri interi e i coefficenti dell'identità di Bezout (x, y).
2. Fast Modular Exponentiation.
   Funzione che consente all'utente di eseguire l'algoritmo di esponenziazione modulare veloce
   - All'utente viene richiesto di inserire 3 numeri interi, la base l'esponente e il modulo n.
3. Miller-Rabin Test
   Funzione che consente all'utente di eseguire il test di Miller-Rabin su un numero intero n.
   - All'utente viene richiesto di inserire un numeri intero su cui effettuare il test e il numero massimo di round da
     far eseguire all'algoritmo. Più il numero di round è alto più il test è accurato per la risposta False, ma anche
     più oneroso in termini di prestazioni. Il numero di round ottimali per ottenere il miglior compromesso è pari a 40,
     ed è consigliato di default. In ogni caso l'utente per usare la funzione deve inserire esplicitamente il numero di
     round. E' consigliato inserire 40 round.
   - Se il numero inserito risulta composto la funzione ritorna il valore True altrimenti False.
4. Prime Number Generator
   Funzione che consente all'utente di generare un numero primo casuale di k bit.
   - All'utente viene richiesto di inserire il numero di bit (un numero intero) con cui generare casualmente il numero
     primo.
   - All'utente viene inoltre richiesto di inserire il numero massimo di round per il test di Miller-Rabin, utilizzato
     dall'algoritmo di generazione casuale. Anche qui è consigliato inserire un numero di round pari a 40.
5. RSA keys Generator
   Funzione che consente all'utente di generare una chiave pubblica e privata RSA.
   - All'utente viene richiesto di inserire il numero di bit (un numero intero), su cui viene generato il modulo n della
     chiave pubblica e privata, e anche se deve essere utilizzata l'ottimizzazione con CRT o meno.
   - Per decidere se utilizzare l'ottimizzazione CRT o meno l'utente deve semplicemnte inserire il carattere 'y' o 'Y'
     se vuole utillizzare CRT oppure 'n' o un qualsiasi altro carattere se non vuole utilizzarlo.
   - All'utente viene inoltre richiesto di inserire il numero massimo di round per il test di Miller-Rabin, utilizzato
     dall'algoritmo di generazione casuale di numeri primi. Anche qui è consigliato inserire un numero di round pari a
     40.
   - La funzione restituisce la chiave pubblica (e, n) e privata (d, n) generate dall'algoritmo.
6. RSA Encryption
   Funzione che consente all'utente di criptare un messaggio m tramite RSA utilizzando una chiave pubblica fornita.
   - All'utente viene richiesto di inserire il messaggio m da criptare (un numero intero) e la chiave pubblica con cui
     effetuare la cifratura, ovvero, l'esponente pubblico e il modulo n.
   - La funzione restituisce il ciphertext generato dall'algoritmo.
7. RSA Decryption
   Funzione che consente all'utente di decifrare un ciphertext c tramite RSA utilizzando una chiave privata fornita.
   - All'utente viene richiesto di inserire il ciphertext c da decifrare (un numero intero) e la chiave privata con cui
     effetuare la cifratura, ovvero, l'esponente privato d il modulo n.
   - La funzione restituisce il messaggio decifrato dall'algoritmo.
8. RSA Decryption With and Without CRT
   Funzione che consente all'utente di testare e confrontare le prestazioni della decifratura RSA con e senza
   l'ottimizzaione CRT basandosi sulla decifratura di un numero i di ciphertext generati casualmente con k bits.
   - All'utente viene richiesto di inserire i numeri primi p e q per il calcolo del modulo n e l'esponente d della
     chiave privata.
   - Succesivamente vengono stampate le chiavi private RSA generate con e senza l'ottimizzazione CRT.
   - All'utente viene inoltre richiesta la dimensione in bits k dei ciphertext che verranno generati casualmente durante
     il test e il numero di iterazioni totali i del test (numero totale di ciphertext da decifrare).
   - La funzione restituisce il tempo di esecuzione totale (in secondi) per la decifratura dei ciphertext per RSA con e
     senza ottimizzazione CRT.
9. Quit.
   Funzione che consente la chiusura del programmma.

# Test di Esempio Effettuato

Per eseguire un test realistico con numeri di dimensione > 10^100 ho deciso di utilizzare i seguenti parametri:

p = 1213107243921127189732367153161244042847242763370141092563454931230196437304208561932419736532241686654101705736136
    5214171711713797974299334871062829803541
q = 1202752425547874888595622079373451212873338780368207543365389998395517985098879789986914690080913161115334681705083
    2096022160146366346391812470987105415233
d = 8948942500927444436822854592177309391966958606588425744549785445648767483962981839093494197326287961679797060891728
    3679875499331574161113854088813275488110588247193077582527278437906504015680623423550067240042466665654232383502922
    215493623289472138866445818789127946123407807725702626644091036502372545139713

Generando quindi un modulo n pari a:

n = 1459067680075833232301869393490706352924018723753571643995818710198734387990053589383695714026701498021218180862924
    6742282815702292207674690654340122488967247240792696998710058129010319931785875366371086235765651050788371429711563
    7342788911463535102712032765166518411726859837988672111837205085526346618740053

Ho dunque testato la decifratutra RSA basando il test su 100 ciphertext scelti casualmente ciascuno formato da 1024 bits.
I risultati ottenuti sono i seguenti:

- RSA Decryption without CRT -
Total Execution Time on 100 Random Ciphertext: 1.789815889542942 seconds

- RSA Decryption with CRT -
Total Execution Time on 100 Random Ciphertext: 0.5414641489185755 seconds

Possiamo notare dunque come la decifratura RSA con ottimizzazione CRT sia quasi quattro volte più veloce rispetto alla
decifratura RSA senza CRT. Possiamo inoltre dire che testando la decifratura RSA con numeri piccoli i due approcci hanno
prestazioni molto simili anche se in alcuni casi CRT mostra comunque un leggerissimo vantaggio, mentre testando la
decifratura RSA con numeri sempre più grandi otteniamo che RSA con ottimizzazione CRT riesce ad essere via via più
veloce fino a risultare al massimo circa quattro volte più veloce dell'approccio senza CRT.

# Author
Elia Mercatanti