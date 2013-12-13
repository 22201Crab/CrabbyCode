CrabbyCode
==========

The code used to control a simple robotic crab.


#include <Servo.h>

Servo servo1;

int dope = A0;
int pot = A1;
int vel = 0;
int lightpin = A2;
int lightmin = 1023;
int lightmax = 0;
int lightval = 0;
int ledr = 11;
int ledg = 10;
int ledb = 9;


void setup ()
{
  servo1.attach(dope);
  Serial.begin(9600);
}



void loop ()
{
  
  vel = (analogRead(pot)); 
  servo1.write(map(lightval,lightmin,lightmax,0,180));
  lightval = analogRead(lightpin);
  Serial.println("  ");
  Serial.println(lightmin);
  Serial.println("  ");
  Serial.println(lightmax);
  
    lightval = analogRead(lightpin);
    
    if (lightval > lightmax)
    {lightmax = lightval;}
    
    if (lightval < lightmin)
    {lightmin = lightval;}

  if (map(lightval,lightmin,lightmax,0,180) > 90)
  {digitalWrite(ledr, LOW);
  digitalWrite(ledg, LOW);
  digitalWrite(ledb, HIGH);}
  
  if (map(lightval,lightmin,lightmax,0,180) <= 90)
  {digitalWrite(ledr, LOW);
  digitalWrite(ledg, HIGH);
  digitalWrite(ledb, LOW);}
  
  
  
  
}


