#include  
 
Servo myservo;
              
 
int pos = 0;    

long FISHFEEDER = 43200000; 
long endtime; 
long now;

void setup() 
{ 
 
  myservo.attach(9); 
  
  myservo.write(0);
  delay(15);
  
}
 
void loop() 
{ 
  now = millis();
  endtime = now + FISHFEEDER;
  
  while(now < endtime) {
   myservo.write(0);
   delay(20000);
   now = millis();   
  }
  

  for(pos = 0; pos < 180; pos += 1)  
  {                             
    myservo.write(pos);     
    delay(15);         
  } 
  for(pos = 180; pos>=1; pos-=1)   
  {                                
    myservo.write(pos);           
    delay(15);                   
  } 
}
