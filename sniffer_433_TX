/*
sketch : sniffer_433_TX       (sister of "sniffer_433_RX")
Author : Peter Matthews (CurlyWurly)   May 2017
Desc   : Copy the "int codez[]=.." line manufactured by the sister sketch "sniffer_433_RX" 
         and paste it into this sketch so that this sketch can spoof the original transmitter.
INFORMATION
************************************************************************************************ 
*** IF THE SKETCH DOESN'T SEEM TO WORK, INCREASE THE REPEAT VALUE TO 50 AND TRY AGAIN, 
*** e.g.  "int codez[] = {50........"
*** N.B. THE CORRECT REPEAT VALUE HAS TO BE VERIFIED BY YOURSELF BY TRIAL AND ERROR 
************************************************************************************************ 
N.B. Connect pin 3 (txpin) to the TX module input
  N.B. Copy the output "int codez[] = ...." from the "Sniffer_433_RX" sketch and paste where marked below
  N.B. The sniffer sketch just outputs a set value of 35 in code[0]. This means that you may have to 
       experiment using a different "repeat" value (usually a value of 15 - 45 is OK) 
  N.B. The code structure is contained from code[0] to code[n] and is defined as:
          code[0] - No. of times to repeat the code
          code[1] - No. of pulses (Hi/low combination) - This means it is half the total number of Hi and Low states 
          code[2] - Wait unit time (Hi and Low states are constructed with multiples of this) 
          code[3] - First HIGH state multiplier - multiply with code[2]   
          code[4] - First LOW  state multiplier - multiply with code[2]   
          ....
          code[n] - last LOW   state multiplier
      The     first  pulse is made up of code[3] and code[4]
      and the second pulse is made up of code[5] and code[6]
*/

#define ldPin      13       //Onboard LED = digital pin 13
#define txPin       3       //Output to RF TX module

//*********************** Copy the output from the "Sniffer_433_RX" sketch here **************************
// int codez[] = 
//**************************** and reference it in "loop()" as tx(codez); ********************************

// Maplin mains switch 1,1 ON
int code1[] = {10,25,434,1,3,1,3,1,3,3,1,1,3,3,1,1,3,3,1,1,3,1,3,1,3,3,1,1,3,3,1,1,3,3,1,1,3,3,1,1,3,3,1,1,3,3,1,1,3,3,1,1,31};
// Maplin mains switch 1,1 OFF
int code2[] = {10,25,432,1,3,1,3,1,3,3,1,1,3,3,1,1,3,3,1,1,3,1,3,1,3,3,1,1,3,3,1,1,3,3,1,1,3,3,1,1,3,3,1,1,3,3,1,1,3,1,3,1,31};
// 1byOne driveway alarm
int code3[] = {41,18,362,1,3,1,3,1,1,3,1,3,1,3,3,1,1,3,1,3,3,1,1,3,3,1,3,1,1,3,1,3,1,3,1,3,1,3,18};
// Friedland PIR alarm
int code4[] = {15,21,754,1,1,1,1,1,1,1,4,1,5,1,4,1,4,1,5,1,6,1,4,1,7,1,4,1,7,1,3,1,5,1,5,1,5,1,5,1,4,1,5,1,27};

void tx(int code);  

//************************************************************
void setup() {
//************************************************************
  pinMode(ldPin, OUTPUT);
  pinMode(txPin, OUTPUT);
  Serial.begin(57600);        // Set up Serial baud rate 
}

//************************************************************
void loop() {
//************************************************************
tx(code1);
delay(2000);
tx(code2);
delay(2000);
tx(code3);
delay(2000);
tx(code4);
delay(2000);
}

//************************************************************
void tx(int code[]){
//************************************************************
  digitalWrite(ldPin, HIGH);     // LED pin on
  for(int j=0; j<code[0]; j=j+1 ){
    for(int i=3; i<((code[1]*2)+3); i=i+1 ){
      if ( ( ( i ) % 2) == 0 ) {
        digitalWrite(txPin, LOW);
      } else {
        digitalWrite(txPin, HIGH);
      };
      for(int k=0; k<code[i]; k=k+1){
        delayMicroseconds(code[2]); 
      };
    };
  };
  digitalWrite(ldPin, LOW);    // LED pin off
}
