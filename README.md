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
