# circuit-code
#include<LiquidCrystal.h>
#include "DHT.h"
#define DHTPIN A0 
#define DHTTYPE DHT11
DHT dht(DHTPIN,DHTTYPE);

const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3,d7 = 2;
LiquidCrystal lcd(rs,en,d4,d5,d6,d7);

void setup()
{
lcd.begin(16,2);
dht.begin();
lcd.print("Welcome!");
delay(2000);
lcd.clear();
}
void loop()
{
float temperatureC = dht.readTemperature();

if(isnan(temperatureC))
{
lcd.setCursor(0,0);
lcd.print("Failed to read");
delay(1000);
lcd.clear();
return;
}
lcd.setCursor(0,0);
lcd.print("Temp:");
lcd.print("27C");
delay(1000);
}
