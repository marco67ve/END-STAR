# END-STAR
Progetto NOVA-IA.BAS e PULSARBN.BAS

## Introduzione

Questi due programmi, scritti nel 1989 in QuickBASIC per PC AT/386, rappresentano sistemi stellari in cui avvengono fenomeni di accrescimento: una nana gialla che alimenta una nana bianca (NOVA-IA.BAS) e una nana bianca che alimenta una stella di neutroni/pulsar (PULSARBN.BAS). Nonostante i limiti tecnici dell’epoca (risoluzione 640×480, capacità computazionale ridotta e assenza di fonti online), le proporzioni utilizzate risultano sorprendentemente vicine ai rapporti fisici reali.

## Scala dei raggi stellari

### NOVA-IA.BAS

Nana gialla: r = 240 px

Nana bianca: r = 2.4 px

Rapporto: 240 / 2.4 = 100 : 1

Nella realtà, una nana gialla tipo solare ha r ˜ 700.000 km mentre una nana bianca tipica ha r ˜ 7.000 km. Il rapporto reale è circa 100 : 1, quindi la rappresentazione è fedele alla scala fisica.

### PULSARBN.BAS

Nana bianca: r = 240 px

Stella di neutroni (pulsar): r = 2.4 px (ma in scala 10×)

Raggio reale simulato ? 0.24 px

Rapporto effettivo reale: 240 / 0.24 = 1000 : 1

Tra una nana bianca (˜7000 km) e una stella di neutroni (˜10–12 km) il rapporto reale è ˜600–700, e in casi estremi può superare 1000. La scelta è dunque fisicamente plausibile.


## Scala delle distanze (300 px tra i centri)

In entrambi i programmi la distanza tra i centri delle due stelle è:

d = 300 px

Confrontata con i raggi delle stelle principali:

Per la nana gialla (240 px): 300/240 = 1.25 raggi stellari

Per la nana bianca (240 px): 300/240 = 1.25 raggi stellari

Questa proporzione si colloca sorprendentemente vicino ai valori attesi nei sistemi binari cataclismici che si trovano al limite di Roche, dove avviene trasferimento di massa.

Il limite di Roche per sistemi di questo tipo cade tipicamente a 1.3 – 2.7 raggi della stella più grande. Il valore scelto (˜1.25) è di fatto al margine: ideale per l’accrescimento simulato dai pixel che “viaggiano” da una stella all’altra.

Pulsar in scala 10×

Nel caso della stella di neutroni, il raggio reale avrebbe dovuto essere troppo piccolo per essere rappresentato graficamente (˜0.24 px). Per questo nel programma è disegnata in scala 10×, mantenendo comunque corretto il rapporto tra le tre classi stellari.

Questa scelta è anotata nel codice d’origine e permette una resa visiva coerente con il fenomeno fisico pur rispettando i vincoli grafici.

## Rappresentazione dei fenomeni astrofisici

### Accrescimento di massa

La sequenza di pixel che si spostano dalla stella più grande a quella compatta rappresenta l’accrescimento oltre il limite di Roche. È un effetto semplificato, ma concettualmente corretto.

#### Nova e Supernova di tipo Ia

In NOVA-IA.BAS la nana bianca raggiunge una soglia (“massa critica”) e viene rappresentata la successiva esplosione tramite cambi di palette e onde d’urto grafiche.

| Fenomeno | Dettaglio | Tecnica BASIC |
|---------|-----------|----------------|
| **Accrescimento** | Pixel che si muovono verso la nana bianca | `PSET` + cancellazione immediata |
| **Lampo di supernova** | Schermo completamente bianco per un istante | Manipolazione palette: `PALETTE 0, 63+256*63+65536*63` |
| **Onda d’urto** | Cerchi in espansione cancellati subito | `CIRCLE` + `CLS` |
| **Perdita di massa della nana gialla** | Raggio gradualmente ridotto | `rNG - SQR(2) * i` |
| **Nebulosa finale** | Punti colorati esclusi dall’area della stella | `DO...LOOP WHILE x^2+y^2 < rNG^2` |

Il risultato è una rappresentazione stilizzata ma molto espressiva di una supernova di tipo Ia.

#### Collasso in buco nero (PULSARBN.BAS)

Nel secondo programma, una pulsar sovraccarica di materia collassa oscurandosi completamente: la schermata si riempie di nero nel punto in cui era la stella compatta.
La scomparsa istantanea è realistica? Sì. Il collasso gravitazionale di una stella di neutroni che supera il limite di Tolman–Oppenheimer–Volkoff avviene in **circa 1 millisecondo**.
Non esiste un’animazione intermedia visibile: da fuori appare come una scomparsa netta.

| Fenomeno | Dettaglio | Tecnica BASIC |
|---------|-----------|----------------|
| **Pulsazione della stella di neutroni** | Alternanza cromatica continua | `IF c=9 THEN c=11 ELSE c=9` + `PAINT` |
| **Accrescimento** | Pixel bianchi che si muovono verso la pulsar | `PSET` |
| **Collasso in buco nero** | La pulsar scompare istantaneamente | `PAINT (xSN,240),0` |
| **Identificazione dell’evento** | Messaggio finale "BUCO NERO" | `LOCATE` + `PRINT` |

## Contesto tecnico (1989)

- QuickBASIC 4.5 senza Internet né fonti approfondite.
- PC AT/386, VGA 640×480, 16 colori.
- Tempi di attesa basati su `TIMER`.
- Uso creativo della palette VGA per ottenere flash e bagliori.
- Logica fisica basata su conoscenze dell’epoca… ma sorprendentemente in linea con l’astrofisica moderna.

## Conclusione

Malgrado la loro semplicità, questi due programmi:
- rispettano proporzioni realistiche tra stelle,
- usano distanze coerenti col limite di Roche,
- simulano correttamente accrescimento, novae, pulsazione e collasso,
- sfruttano abilmente la grafica VGA per rendere fenomeni complessi,
- dimostrano un’inaspettata intuizione astrofisica.

Un piccolo frammento del 1989 che, rivisto oggi, appare molto più raffinato di quanto avrebbe potuto sembrare all’epoca.
