#include <LiquidCrystal.h>
double v = 0.0;
double v2 = 0.0;
double F = 0.0;
double Rs = 0.0;
double w = 0.0; 


const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

void setup() {
 
  lcd.begin(16, 2);
  pinMode(A0,INPUT);
Serial.begin(9600);
 
}

void loop() {
  v=(analogRead(A0));
  v2 = (v*5)/1023; 
  Rs = 15*(5/v2 - 1);
  F = pow(Rs/6.0075,-1/0.701);
  w = ((F/9.81)*1000);
  
  lcd.clear();
  lcd.setCursor(3,0);
  lcd.print("F:");
  lcd.print(F,3);
  lcd.print(" N");
  lcd.setCursor(3,2);
  lcd.print("masa:");
  lcd.print(w,2);
  lcd.print(" g");
  lcd.print("");
  delay(500);
  lcd.clear();
}
