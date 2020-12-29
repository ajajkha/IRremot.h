#include <IRremote.h>
#define irPin 3
IRrecv irrecv(irPin);
decode_results results;
#define r1 4
int relay1 = LOW;
#define r2 5
int relay2 = LOW;
#define r3 6
int relay3 = LOW;
#define r4 7
int relay4 = LOW;
#define r5 8
int relay5 = LOW;
#define r6 9
int relay6 = LOW;
#define r7 10
int relay7 = LOW;
#define r8 12
int relay8 = LOW;
void setup() 
{
    irrecv.enableIRIn();
    pinMode(r1, OUTPUT); 
    pinMode(r2, OUTPUT);
    pinMode(r3, OUTPUT);
    pinMode(r4, OUTPUT); 
    pinMode(r5, OUTPUT);
    pinMode(r6, OUTPUT); 
    pinMode(r7, OUTPUT);
    pinMode(r8, OUTPUT);     
}
void loop() {
   if (irrecv.decode(&results)) {
      switch (results.value) {
                    case 33441975:
            digitalWrite(r1,0);
            digitalWrite(r2,0);
            digitalWrite(r3,0);
            digitalWrite(r4,0);
            digitalWrite(r5,0);
            digitalWrite(r6,0);
            digitalWrite(r7,0);//all off
            digitalWrite(r8,0);
            delay(250);
            break;        
            case 33444015:
            relay1 = ~ relay1;
            digitalWrite(r1,relay1);
            delay(250);
            break;
            case 33478695:
            relay2 = ~ relay2;
            digitalWrite(r2,relay2);
            delay(250);
            break;
            case 33486855:
            relay3 = ~ relay3;
            digitalWrite(r3,relay3);
            delay(250);
            break;
            case 33435855:
            relay4 = ~ relay4;
            digitalWrite(r4,relay4);
            delay(250);
            break;
            case 33468495:
            relay5 = ~ relay5;
            digitalWrite(r5,relay5);
            delay(250);
            break;
            case 33452175:
            relay6 = ~ relay6;
            digitalWrite(r6,relay6);
            delay(250);
            break; 
            case 33423615:
            relay7 = ~ relay7;
            digitalWrite(r7,relay7);
            delay(250);
            break;
            case 33484815:
            relay8 = ~ relay8;
            digitalWrite(r8,relay8);
            delay(250);
            break;                      
           }
 
   irrecv.resume();
   }
}
