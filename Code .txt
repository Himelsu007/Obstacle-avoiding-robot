const int trig = 6;
const int echo = 5;
const int leftFrwrd = 10;
const int leftBack = 11;
const int rightFrwrd = 8;
const int rightBack = 9;

int duration = 0;
int distance = 0;

void setup() 
{
  pinMode(trig , OUTPUT);
  pinMode(echo , INPUT);
  pinMode(leftFrwrd , OUTPUT);
  pinMode(leftBack , OUTPUT);
  pinMode(rightFrwrd , OUTPUT);
  pinMode(rightBack , OUTPUT);
  pinMode(13 , OUTPUT);
  digitalWrite(13 , HIGH);
  pinMode(10 , OUTPUT);
  digitalWrite(10 , LOW);
  Serial.begin(9600);

}

void loop()

{
  
digitalWrite(trig, LOW);
delayMicroseconds(2);
digitalWrite(trig, HIGH);
delayMicroseconds(10);
digitalWrite(trig, LOW);
duration = pulseIn(echo, HIGH);
distance= (duration*0.034/2);

Serial.print("Distance: ");
Serial.println(distance);
  
  if(distance>20)
  {
    digitalWrite(leftFrwrd , HIGH);
    digitalWrite(leftBack , LOW);
    digitalWrite(rightFrwrd , HIGH);
    digitalWrite(rightBack , LOW);
    delay(100);
  }
  else 
 
  {
    digitalWrite(leftFrwrd , LOW);
    digitalWrite(leftBack , HIGH);
    digitalWrite(rightFrwrd , HIGH);
    digitalWrite(rightBack ,LOW );
  }
 
}
