#include <IRremote.h>
#define irPin 3
IRrecv irrecv(irPin);
decode_results results;
#define r1 5
int relay1 = LOW;
#define r2 6
int relay2 = LOW;
#define r3 7
int relay3 = LOW;
void setup() 
{
    irrecv.enableIRIn();
    pinMode(r1, OUTPUT); 
    pinMode(r2, OUTPUT);
    pinMode(r3, OUTPUT);   
}
void loop() {
   if (irrecv.decode(&results)) {
      switch (results.value) {
                    case 33441975:
            digitalWrite(r1,0);
            digitalWrite(r2,0);  //all off
            digitalWrite(r3,0);
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
           }
 
   irrecv.resume();
   }
}
