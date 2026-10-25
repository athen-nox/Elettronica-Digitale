# Relazione del primo progetto di Elettronica Digitale

di Francescantonio S., Gabriel A. P., Cosmo S.
Ottobre 2026,

Di seguito verranno trattati brevemente la teoria alla base degli adder, VHDL e nel dettaglio il processo di realizzazione di un CSA a 16 bit proposto come traccia per il primo progetto del corso di Elettronica Digitale (LT Ing. Informatica, Dimes, Unical, docente Stefania Perri).

# Introduzione

## I circuiti addizionatori

Gli addizionatori o adder in inglese, sono un tipo di elemento circuitale fondamentale nei sistemi digitali, poiché responsabili di operazioni matematiche chiave come la somma, sottrazione (tramite Complemento a Due), moltiplicazione e divisione hardware, incremento. 
Sono presenti ad esempio in circuiti combinatori come le ALU (Arithmetic Logic Unit), in unità dedicate per operazioni specifiche di supporto come l'incremento del Program Counter o il calcolo degli indirizzi nelle Unità di Generazione degli Indirizzi (AGU - Address Generation Unit) per l'accesso alla memoria, o ancora sono presenti massicciamente nelle GPU per gestire i calcoli geometrici, vettoriali e di rendering 3D.
Data la loro importanza, nel corso degli anni sono state proposte diverse soluzioni circuitali per minimizzare il ritardo combinatorio, da cui dipende la massima frequenza operativa in un sistema sincrono.

Il circuito fondamentale alla base degli addizionatori più complessi è il Full-Adder, che si occupa di sommare tre bit, ovvero la coppia di bit A e B e il riporto in ingresso Cin (Carry-in), e produce due output, il risultato della somma S e il riporto in uscita Cout (Carry-out).

Una possibile soluzione è il Ripple-Carry Adder (RCA), che esegue la somma di due numeri in notazione binaria, sommando bit a bit, dalla coppia meno significativa a quella più significativa, procedendo verso sinistra, propagando di volta in volta il riporto, in modo analogo all'addizione in colonna che gli umani svolgono a mano. Questo metodo gode del vantaggio della semplicità implementativa, ma soffre dell'estrema lentezza causata proprio dalla propagazione del riporto.

Un'architettura più complessa e costosa, ma molto più veloce, è il Carry-Select Adder (CSA), che mira a parallelizzare il calcolo ignorando in un primo momento il riporto, che solo alla fine dell'operazione servirà per riportare il risultato corretto. L'idea è quella di dividere gli n bit da sommare in p blocchi da m bit, secondo la relazione n = p * m. Il primo blocco è composto da un RCA, mentre i blocchi  dal secondo all'ultimo sono composti da due RCA che eseguono in parallelo la somma dei medesimi bit, uno con il segnale Cin = 1 e l'altro con Cin = 0. Il risultato verrà selezionato da un multiplexer, che riceverà come segnale di selezione il riporto del blocco precedente. 

## VHDL e Vivado

Il VHDL (acronimo di VHSIC Hardware Description Language, dove "VHSIC" è la sigla per Very High Speed Integrated Circuits), è un linguaggio di descrizione dell'hardware, in grado di modellare il comportamento e la struttura di sistemi digitali a diversi livelli di astrazione, spaziando dal livello di sistema fino a quello delle porte logiche.

Vivado è un ambiente di sviluppo integrato sviluppato da AMD (in precedenza da Xilinx) per progettare, testare e programmare circuiti integrati programmabili, chiamati FPGA e SoC. La suite di Vivado permette di scrivere codice VHDL, simulare il comportamento del circuito e tradurre il codice descrittivo di alto livello in uno schema concreto di porte logiche elementari, multiplexer, registri e interconnessioni (sintesi del circuito).
# Progettazione

Per la realizzazione del CSA a 16 bit, dopo un primo confronto, supportato da strumenti tradizionali come la lavagna, si è giunti all'unanimità alla scelta di strutturare il progetto a moduli seguendo un approccio bottom-up, che sono stati sviluppati nei seguenti file VHDL:

- FullAdder.vhd
- RCA4.vhd
- RCA4_Block.vhd
- CSA16.vhd
- CSA16_tb.vhd

Per l'intero progetto si è fatto riferimento esclusivamente alla libreria standard IEEE (in particolare il package IEEE.STD_LOGIC_1164.ALL) e ai tipi primitivi BIT e BIT_VECTOR.
L'implementazione è affrontata nel dettaglio per ogni componente nei paragrafi successivi.

## FullAdder

## RCA4

## RCA4_Block

Una volta creati i sommatori possiamo configurare una struttura intermedia di supporto per semplificare l'implementazione del nostro CSA. Questo blocco è composto dai due sommatori 
## CSA16
# Simulazione

## CSA16_tb
# Sintesi

# Conclusioni
