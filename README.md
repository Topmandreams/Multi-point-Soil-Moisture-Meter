# Multi-point-Soil-Moisture-Meter
This meter comprises an Arduino Microcontroller with soil moisture sensor 

#include <LCD_I2C.h>
LCD_I2C lcd(0x27, 16, 2);

int analogpin1=A0; int analogpin2=A1;
int moisture1;     int moisture2;
int percentage1;   int percentage2;
int map_low1=0.00; int map_low2=0.00;
int map_high1=5.00;int map_high2=5.00;

int analogpin3=A2; int analogpin4=A3;
int moisture3;     int moisture4;
int percentage3;   int percentage4;
int map_low3=0.00; int map_low4=0.00;
int map_high3=5.00;int map_high4=5.00;

int analogpin5=A6; int analogpin6=A7;
int moisture5;     int moisture6;
int percentage5;   int percentage6;
int map_low5=0.00; int map_low6=1023.00;
int map_high5=5.00;int map_high6=304.00;

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  lcd.begin();  
  lcd.backlight();

     lcd.setCursor(3, 0); 
     lcd.print("--DIGITAL--");

     lcd.setCursor(2, 1);
     lcd.print("MULTI-SENSOR");
     delay(2000);
     
     lcd.setCursor(2, 0);
     lcd.print("SOIL MOISTURE");
     lcd.setCursor(2, 1);
     lcd.print("  METER     ");
     
     lcd.print(" ");
     delay(2000);
     lcd.clear();
}
void loop() {
moisture1=analogRead(analogpin1); moisture2=analogRead(analogpin2);
moisture3=analogRead(analogpin3); moisture4=analogRead(analogpin4);
moisture5=analogRead(analogpin5); moisture6=analogRead(analogpin6);

percentage1=map(moisture1,map_low1,map_high1,0,97); percentage2=map(moisture2,map_low2,map_high2,0,97);
percentage3=map(moisture3,map_low3,map_high3,0,97); percentage4=map(moisture4,map_low4,map_high4,0,97);
percentage5=map(moisture5,map_low5,map_high5,0,97); percentage6=map(moisture6,map_low6,map_high6,0,97);

   Serial.println(moisture6);

   if(percentage1>=97){
      lcd.setCursor(0, 0);   
    lcd.print("A:");
    lcd.setCursor(2, 0);
    lcd.print("100");
    lcd.print("%");
    lcd.print("   ");
}

if(percentage2>=97){
      lcd.setCursor(7, 0);   
    lcd.print("B:");
    lcd.setCursor(9, 0);
    lcd.print("100");
    lcd.print("%");
    lcd.print("   ");
}

if(percentage3>=97){
      lcd.setCursor(0, 1);   
    lcd.print("C:");
    lcd.setCursor(2, 1);
    lcd.print("100");
    lcd.print("%");
    lcd.print(" ");
}

if(percentage4>=97){
    lcd.setCursor(7, 1);   
    lcd.print("D:");
    lcd.setCursor(9, 1);
    lcd.print("100");
    lcd.print("%");
    lcd.print("  ");
}
    delay(3000);

    if(percentage5>=97){
    lcd.setCursor(0, 1);   
    lcd.print("E:");
    lcd.setCursor(2, 1);
    lcd.print("100");
    lcd.print("%");
    lcd.print(" ");
}

if(percentage6>=97){
    lcd.setCursor(7, 1);   
    lcd.print("F:");
    lcd.setCursor(9, 1);
    lcd.print("100");
    lcd.print("%");
    lcd.print("  ");
}

delay(3000);

   if(percentage1<97){
    lcd.setCursor(0, 0);   
    lcd.print("A:");
    lcd.setCursor(2, 0);
    lcd.print(percentage1 );
    lcd.print("%");
    lcd.print("   ");
   }
 if(percentage2<97){
    lcd.setCursor(7, 0);   
    lcd.print("B:");
    lcd.setCursor(9, 0);
    lcd.print(percentage2 );
    lcd.print("%");
    lcd.print("   ");
}
 if(percentage3<97){
    lcd.setCursor(0, 1);   
    lcd.print("C:");
    lcd.setCursor(2,1);
    lcd.print(percentage3 );
    lcd.print("%");
    lcd.print("   ");
}
 if(percentage4<97){
    lcd.setCursor(7, 1);   
    lcd.print("D:");
    lcd.setCursor(9,1);
    lcd.print(percentage4 );
    lcd.print("%");
    lcd.print("   ");
}
    delay(2000);

     if(percentage5<97){
    lcd.setCursor(0, 1);   
    lcd.print("E:");
    lcd.setCursor(2,1);
    lcd.print(percentage5 );
    lcd.print("%");
    lcd.print("   ");
    }
 if(percentage6<97){
    lcd.setCursor(7, 1);   
    lcd.print("F:");
    lcd.setCursor(9,1);
    lcd.print(percentage6 );
    lcd.print("%");
    lcd.print("   ");
}
delay(2000);
}
