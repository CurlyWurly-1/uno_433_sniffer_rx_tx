# uno_433_sniffer_rx_tx
A pair of sketches to decrypt and spoof a static 433 Mhz transmission

Using the "RX" sketch, a "int codez[]=.." line is output to the serial bus whenever a validated 433 Mhz transmission is received.
Copy this line into the "TX" sketch, and you can adapt the the "TX" sketch to spoof the original transmission.

For the "RX" sketch, connect pin 2 to the receiver module output. 

N.B. The MSG1 version has now been improved to ignore glitches,  and also to enable output during the last "low" state - it seems to work quite well, so I would use this one from now on, but be aware that the last low phase value will be different for the low phase value between each pulse. 

For the "TX" sketch, connect pin 3 to the transmitter module input.
