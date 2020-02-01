
Working:
The design consists of two RGB leds. No. 2 is for output and the other one (No. 1)is for reflecting light on LDR. When an object is placed near the No. 1 RGB led, the object absorbs all the other colours except its own colour. For example a red object will absorb all other colours falling onto it except red. Thus red is reflected on the LDR and its resistance changes. This input is continuous taken. We can thus light up the second led as RED and print “Colour is Red” onto the serial monitor.

Design:  
Three resistors are in series with the LDR and the two RGB leds.  no. 1 RGB is connected to digital pins 2,3,4 of Arduino Uno (R-2,G-3,B-4). no. 2  RGB is connected to digital pins 8,9,10 of Arduino (R-8,G-9,B-10). LDR’s anode is connected to 5V of Arduino Uno.

Calculations :
Maximum current in the LDR or RGB led is: 20mA (datasheet)
Working voltage = 2V (datasheet)
Hence by ohms law,
R=(5-2)/20m
   = 150 ohms
Therefore, I have chosen resistor of 200 ohms for safety.

int redled=2;
int greenled=3;
int blueled=4;


int ldr= A0;
int red;
int blue;
int green;

int redopvalue;
int greenopvalue;
int blueopvalue;

int redop=8;
int greenop=9;
int blueop=10;

 
 void setup() {
  // put your setup code here, to run once:
pinMode(redled,OUTPUT);
pinMode(greenled,OUTPUT);
pinMode(blueled,OUTPUT);

pinMode(ldr,INPUT);

pinMode(redop,OUTPUT);
pinMode(greenop,OUTPUT);
pinMode(blueled,OUTPUT);
   
pinMode(templed,OUTPUT);
   
Serial.begin(9600);
}

void loop() {
  // put your main code here, to run repeatedly:


  digitalWrite(redled,HIGH);
  delay(40);
  red=analogRead(ldr);
  delay(10);
  digitalWrite(redled,LOW);

  digitalWrite(greenled,HIGH);
  delay(40);
  green=analogRead(ldr);
  delay(10);
  digitalWrite(greenled,LOW);

  digitalWrite(blueled,HIGH);
  delay(40);
  blue=analogRead(ldr);
  delay(10);
  digitalWrite(blueled,LOW);

  if(red>blue && red>green)
  {
    redopvalue=HIGH;
    Serial.println("Colour is Red");
  }
  else
  {
    redopvalue=LOW;
  }

  if (green>blue && green>red)
  {
    greenopvalue=HIGH;
    Serial.println("Colour is Green");
  }
  else
  {
    greenopvalue=LOW;
  }

  if (blue>red && blue>green)
  {
    blueopvalue=HIGH;
    Serial.println("Colour is Blue");
  }
  else
  {
    blueopvalue=LOW;
  }

  digitalWrite(redop,redopvalue);
  digitalWrite(greenop,greenopvalue);
  digitalWrite(blueop,blueopvalue);

  
}
