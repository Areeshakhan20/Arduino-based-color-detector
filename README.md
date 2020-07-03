# Arduino-based-color-detector
#include <LiquidCrystal.h>
// initialize the library with the numbers of the interface pins
LiquidCrystal lcd(13, 12, 11, 10, 9, 8);
#define S0 2
#define S1 3
#define S2 4
#define S3 5
#define sensorOut 6
int Rfre = 0,Gfre = 0,Bfre = 0;

void setup()
{
// set up the LCD's number of columns and rows
  lcd.begin(16,2);
  pinMode(S0, OUTPUT);
  pinMode(S1, OUTPUT);
  pinMode(S2, OUTPUT);
  pinMode(S3, OUTPUT);
  pinMode(sensorOut, INPUT);
  // Setting frequency-scaling to 20%
  digitalWrite(S0,HIGH);
  digitalWrite(S1,LOW);
  lcd.setCursor(0,0);
  lcd.print("COLOUR DETECTION");
  delay(4000);
}

void loop() {
  // Setting red filtered photodiodes to be read
  digitalWrite(S2,LOW);
  digitalWrite(S3,LOW);
  // Reading the output frequency
  Rfre = pulseIn(sensorOut, LOW);
  delay(100);
  // Setting Green filtered photodiodes to be read
  digitalWrite(S2,HIGH);
  digitalWrite(S3,HIGH);
  // Reading the output frequency
  Gfre = pulseIn(sensorOut, LOW);
  delay(100);
  // Setting Blue filtered photodiodes to be read
  digitalWrite(S2,LOW);
  digitalWrite(S3,HIGH);
  // Reading the output frequency
  Bfre = pulseIn(sensorOut, LOW);
  delay(100);
  lcd.setCursor(0,1);
  lcd.print("                ");
if((Rfre>=24 && Rfre<=25)&&(Gfre>=20 && Gfre<=21)&&(Bfre>=8 && Bfre<=9)){
  lcd.setCursor(0,0);
  lcd.print("COLOUR DETECTED ");
  lcd.setCursor(0,1);
  lcd.print("  LIGHT GREEN   ");//printing name
  delay(2500);
}
if((Rfre>=20 && Rfre<=21)&&(Gfre>=20 && Gfre<=21)&&(Bfre>=6 && Bfre<=7)){
  lcd.setCursor(0,0);
  lcd.print("COLOUR DETECTED ");
  lcd.setCursor(0,1);
  lcd.print("   LIGHT BLUE   ");//printing name
  delay(2500);
}
if((Rfre>=8 && Rfre<=9)&&(Gfre>=11 && Gfre<=12)&&(Bfre>=4 && Bfre<=5)){
  lcd.setCursor(0,0);
  lcd.print("COLOUR DETECTED ");
  lcd.setCursor(0,1);
  lcd.print("     YELLOW    ");//printing name
  delay(2500);
}
if((Rfre>=31 && Rfre<=32)&&(Gfre>=33 && Gfre<=34)&&(Bfre>=10 && Bfre<=11)){
  lcd.setCursor(0,0);
  lcd.print("COLOUR DETECTED ");
  lcd.setCursor(0,1);
  lcd.print("  DARK  GREEN   ");//printing name
  delay(2500);
}
if((Rfre>=11 && Rfre<=12)&&(Gfre>=30 && Gfre<=31)&&(Bfre>=5 && Bfre<=7)){
  lcd.setCursor(0,0);
  lcd.print("COLOUR DETECTED ");
  lcd.setCursor(0,1);
  lcd.print("      RED       ");//printing name
  delay(2500);
}
if((Rfre>=8 && Rfre<=9)&&(Gfre>=24 && Gfre<=25)&&(Bfre>=5 && Bfre<=6)){
  lcd.setCursor(0,0);
  lcd.print("COLOUR DETECTED ");
  lcd.setCursor(0,1);
  lcd.print("      PINK      ");//printing name
  delay(2500);
}
if((Rfre>=6 && Rfre<=7)&&(Gfre>=18 && Gfre<=19)&&(Bfre>=4 && Bfre<=5)){
  lcd.setCursor(0,0);
  lcd.print("COLOUR DETECTED ");
  lcd.setCursor(0,1);
  lcd.print("     ORAGNE     ");//printing name
  delay(2500);
}
if((Rfre>=23 && Rfre<=24)&&(Gfre>=37 && Gfre<=38)&&(Bfre>=9 && Bfre<=10)){
  lcd.setCursor(0,0);
  lcd.print("COLOUR DETECTED ");
  lcd.setCursor(0,1);
  lcd.print("   DARK BROWN   ");//printing name
  delay(2500);
}
else{
  lcd.setCursor(0,0);
  lcd.print("COLOUR DETECTION");
  lcd.setCursor(0,1);
  lcd.print("R");//printing name
  lcd.print(Rfre);//printing RED color frequency
  lcd.print("  ");
  lcd.setCursor(6,1);
  lcd.print("G");//printing name
  lcd.print(Gfre);//printing RED color frequency
  lcd.print("  ");
  lcd.setCursor(12,1);
  lcd.print("B");//printing name
  lcd.print(Bfre);//printing RED color frequency
  lcd.println("  ");
}



  
}              
