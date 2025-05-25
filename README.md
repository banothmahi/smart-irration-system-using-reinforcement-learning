# smart-irration-system-using-reinforcement-learning
#include <LiquidCrystal.h>
const int rs = 13, en = 12, d4 = 11, d5 = 10, d6 = 9, d7 = 8;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
int soil=2;
int relay=3;
void setup()
{
 pinMode(soil,INPUT);pinMode(relay,OUTPUT);digitalWrite(relay,HIGH);
 lcd.begin(16, 2);
 lcd.clear();lcd.print("SMART IRRIGATION");
 lcd.setCursor(0,1);lcd.print("SYSTEM USING ARDUINO ");delay(1000);
 Serial.begin(9600);delay(1000);
}
void loop()
{
 int soilval=digitalRead(soil);delay(1000);
 if(soilval==LOW)
 {
 lcd.clear();lcd.print("SOIL:WET");delay(1000);
 lcd.setCursor(0,1);lcd.print(" MOTOR OFF");delay(1000);
 digitalWrite(relay,HIGH);delay(1000);
 }
 if(soilval==HIGH)
 {
 lcd.clear();lcd.print("SOIL:DRY");delay(1000);
 lcd.setCursor(0,1);lcd.print(" MOTOR ON");delay(1000);
 digitalWrite(relay,LOW);delay(1000);
 }
}
