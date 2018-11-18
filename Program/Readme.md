#include <SoftwareSerial.h>

const int rxPin = 0;
const int txPin = 1;               
SoftwareSerial mySerial(rxPin, txPin);

int ac=4;
int light=5;
int fan=6;
int tv=7;
String data;


void setup() {
  Serial.begin(9600);    // because to check your program or circiut is working or not

   mySerial.begin(9600);

   pinMode(ac, OUTPUT);       // write your commands
   pinMode(light, OUTPUT);
   pinMode(fan, OUTPUT);
   pinMode(tv, OUTPUT);

   digitalWrite(ac, LOW);     // things to be switched off
   digitalWrite(light, LOW);
   digitalWrite(fan, LOW);
   digitalWrite(tv, LOW);


  // put your setup code here, to run once:

}

void loop() {
  int i=0;       // declare your int, char etc.

    char ch=0;

    data="";

    while(1)

    { 

      while(mySerial.available()<=0);

      ch = mySerial.read();

      if(ch=='#')         //condition for choices

      break;

      data+=ch;

    }

   Serial.println(data);

    

    if(data=="*turn on AC")     // start your commands gives to the cicurit

    { 

      digitalWrite(ac,HIGH);

      Serial.println("ac on");

    }

    else if(data=="*turn off AC")

    {

      digitalWrite(ac,LOW);

      Serial.println("ac off");

    }

    else if(data=="*turn on light")

    {

      digitalWrite(light,HIGH);

      Serial.println("light on");

    }

    else if(data=="*turn off light")

    {

      digitalWrite(light,LOW);

      Serial.println("light off");

    }

    else if(data=="*turn on fan")

    {

      digitalWrite(fan,HIGH);

      Serial.println("fan on");

    }

    else if(data=="*turn off fan")

    {

      digitalWrite(fan,LOW);

      Serial.println("fan off");

    }

    else if(data=="*turn on TV")

    {

      digitalWrite(tv,HIGH);

      Serial.println("tv on");

    }

    else if(data=="*turn on TV")

    {

      digitalWrite(tv,LOW);

      Serial.println("tv off");

    }

    else if(data=="*turn on all")

    {

      digitalWrite(ac,HIGH);

      digitalWrite(light,HIGH);

      digitalWrite(fan,HIGH);

      digitalWrite(tv,HIGH);

      Serial.println("all on");

    }

    else if(data=="*turn off all")

    {

      digitalWrite(ac,LOW);

      digitalWrite(light,LOW);

      digitalWrite(fan,LOW);

      digitalWrite(tv,LOW);

      Serial.println("all off");

    

    }

  
  

}
