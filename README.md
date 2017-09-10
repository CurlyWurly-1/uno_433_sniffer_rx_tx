# uno_433_sniffer_rx_tx
A pair of sketches to decrypt and spoof a static 433 Mhz transmission

Using the "RX" sketch, a "int codez[]=.." line is output to the serial bus whenever a validated 433 Mhz transmission is received.
Copy this line into the "TX" sketch, and you can adapt the the "TX" sketch to spoof the original transmission.

For the "RX" sketch, connect pin 2 to the receiver module output. N.B. The MSG1 version has been improved to to ignore glitches and enable output during the last "low" state - it seemsto work quite well - so I woudl use his one from now on. but be aware that the last low phase value will be different for the last pulse train. 

For the "TX" sketch, connect pin 3 to the transmitter module input.
