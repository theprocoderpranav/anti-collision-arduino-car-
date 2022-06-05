# anti-collision-arduino-car-
This code is for an anti-collision car that does not crash into any objects around it. To do this, it does require ardiuo ide. Here is the website for downloading it 
https://www.arduino.cc/en/software

If you are in Arduino IDE, here is the code you should copy.
(Down) 


#include <Servo.h>
#include <Ultrasonic.h> 
int trig=2, echo=5;
Ultrasonic US (2,5);
Servo Coder;

void setup () 
{
  Serial.begin(9600);
  Pranav.attach(A5);
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
 Pranav.write(90);
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
