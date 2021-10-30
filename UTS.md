# UTS.PROJECT.ARDUINO.SENSOR.SUHU.DINI19
// PROJECT SENSOR SUHU
// DINI AMELIA (1197070019)

#include <LiquidCrystal.h>

LiquidCrystal lcd (2, 3, 4, 5, 6, 7);

int dataADC;
float suhu, vin;


void setup() 
{
  pinMode(A0, INPUT);
  pinMode (9, OUTPUT);
  
  Serial.begin (9600);
  lcd.begin(16, 2);
  lcd.setCursor (0, 0);
  lcd.print ("Temperatur 'C : ");
}

void loop()
{
  dataADC = analogRead (A0);
  vin = (dataADC/1024.0) * 5.0;
  suhu = (vin - .5) * 100;
  
  lcd.setCursor (2,2);
  lcd.print(suhu);
  
  if (suhu > 30.00) {
  	digitalWrite(9, HIGH);
  	delay(100); // Wait for 100 millisecond(s)
  }
  
  else {
    digitalWrite(9, LOW);
  	delay(100); // Wait for 100 millisecond(s)
  }
}
