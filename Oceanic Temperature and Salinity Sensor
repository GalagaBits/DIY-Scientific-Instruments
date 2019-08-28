#include <OneWire.h>
#include <DallasTemperature.h>
#include <Wire.h>
#include <LCD.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C  lcd(0x27,2,1,0,4,5,6,7);

#define ONE_WIRE_BUS 2


OneWire oneWire(ONE_WIRE_BUS);

DallasTemperature sensors(&oneWire);

 float Celcius=0;
 float Fahrenheit=0;
 
 
void setup()
{
  lcd.begin (16,2); // for 16 x 2 LCD module
  lcd.setBacklightPin(3,POSITIVE);
  lcd.setBacklight(HIGH);
  Serial.begin(9600);
  sensors.begin();
}

void loop()
{ 
  int d_Solids = analogRead(A0);
  sensors.requestTemperatures(); 
  Celcius=sensors.getTempCByIndex(0);
  Fahrenheit=sensors.toFahrenheit(Celcius);
  Serial.print(" C  ");
  Serial.println(Celcius);
  Serial.print(" F  ");
  Serial.println(Fahrenheit);
  Serial.print(" %S ");
  Serial.println(d_Solids);
  lcd.clear();
  lcd.home();
  lcd.print("Temp(F): ");
  lcd.print(Fahrenheit);
  lcd.setCursor(0,1);
  lcd.print("Salt Value: ");
  lcd.print(d_Solids);
  
  delay(1000);
}
