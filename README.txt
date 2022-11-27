# anti-collision-arduino-car-
Here is the code for a car that will not bump into any obstacles. Make sure you have Arduino IDE 
Download Link https://www.arduino.cc/en/software
Get library from Eric Simoes
Parts:
Chassis 
Servo 
Motor Driver 
Dc Motors(Beau Motors) 
Micro Servo
Jumper Cables(Male to Male and Male to Female) 
Battery Comaprtment
two 3.7V batteries 
Ultrasonic Sensor ( hr SC04)



Now Upload the code into Arduino IDE 


#include <Servo.h>
#include <Ultrasonic.h> 
int trig=2, echo=5;
Ultrasonic US (2,5);
Servo Coder;

void setup () 
{
  Serial.begin(9600);
  Coder.attach(A5);
  int reader = US.read();
  pinMode(6,OUTPUT); 
  pinMode(11,OUTPUT);
  pinMode(12,OUTPUT);
  pinMode(13,OUTPUT);
}
void loop ()
{
 int reader = US.read();
 Serial.println(reader);
 Serial.println();  
 Coder.write(90);
 if  (reader < 30)
 {
 halt();
 delay(500);
 Coder.write(0);
 delay(500);
 int l=US.read();
 Coder.write(180);
 delay(500);
 int r=US.read();
 Coder.write(90);
 delay(500);
 Coder.write(45);
 delay(500);
 Serial.println(l);
 Coder.write(135);
 delay(500);
 Serial.println(r);

 if(l > r) 
 {
  right();
  delay(300);
  forward();
 }
 else 
 {
  left();
  delay(300);
  forward();
 }
 }
 else
 {
  forward();
 }
 
}
void forward() 
{
analogWrite(6,200);
analogWrite(11,200);
digitalWrite(12,LOW);
digitalWrite(13,HIGH);
Serial.println("forward");
}
void backward () 
{
 analogWrite(6,200);
 analogWrite(11,200);
 digitalWrite(12,HIGH);
 digitalWrite(13,LOW);
 Serial.println("backward");
}
void left() 
{
 analogWrite(6,200);
 analogWrite(11,200);
 digitalWrite(12,HIGH);
 digitalWrite(13,HIGH);
 Serial.println("left");
}
void right () 
{
 analogWrite(6,200);
 analogWrite(11,200);
 digitalWrite(12,LOW);
 digitalWrite(13,LOW);
 Serial.println("right");
  
}
void halt () 
{
analogWrite(6,0);
analogWrite(11,0);
Serial.println("halt");
}
