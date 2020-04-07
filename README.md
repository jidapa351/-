#include <Servo.h>
#define BLYNK_PRINT Serial
#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>

Servo myservo;
char auth[] = "ZG_I6I1A-OQjVIjdmHU6E4EJB-oLgGq2";
char ssid[] = "ON&AOY 5G ";
char pass[] = "0624633720";
//int param;

void setup()
{
  // Debug console
  Serial.begin(9600);
  myservo.attach(D6);
  Blynk.begin(auth, ssid, pass);
}

void loop()
{
  Blynk.run();
}

BLYNK_WRITE(V5) // Button Widget writes to Virtual Pin V5
{
  int i = param.asInt();
  if(i==1){
    Servoon();
    }
}

void Servoon() {
  int pos = 1;
  for (pos = 1; pos <= 60; pos += 1) {
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(15);                       // waits 15ms for the servo to reach the position
  }
}
