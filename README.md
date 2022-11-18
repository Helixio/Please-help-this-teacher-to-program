# Please-help-this-teacher-to-program
Hi, I'm new to programming and I'm building a robot to blow out candles for my students. but the code is not working as it should

int in1 = 3, in2 = 4, in3 = 5, in4 = 6;
int enable1 = 10, enable2 = 11;
int distancia;
int tiempo;
int TRIGGER = 9, ECHO = 8;
int luz;
int cny_LED = 2;

void setup()
{
pinMode(cny_LED, OUTPUT); 
digitalWrite(cny_LED,HIGH);
  
pinMode(in1, OUTPUT);
pinMode(in2, OUTPUT);
pinMode(in3, OUTPUT);
pinMode(in4, OUTPUT);
analogWrite(enable1, 120);
analogWrite(enable2, 120);
Serial.begin(9600);
pinMode(TRIGGER, OUTPUT); 
pinMode(ECHO, INPUT); 
}
void loop()
{
do {
derecha();
delay(200);
distancia=distancia_medida();
} while (distancia>=20);
do {
adelante();
luz = analogRead(A1);
distancia = distancia_medida();
delay(80);
} while (luz>900 || distancia<=20);
detener();
delay(1000);
izquierda();
delay(800);
adelante();
delay(300);
detener();
delay(2000);


}
int distancia_medida() {
digitalWrite(TRIGGER, LOW);
delayMicroseconds(2);
digitalWrite(TRIGGER, HIGH);
delayMicroseconds(10);
digitalWrite(TRIGGER, LOW);

tiempo = pulseIn(ECHO, HIGH);

distancia = tiempo / 58;



return distancia;
}
void detener() {
digitalWrite(in1, LOW);
digitalWrite(in2, LOW);
digitalWrite(in3, LOW);
digitalWrite(in4, LOW);
}
void izquierda() {
digitalWrite(in1, HIGH);
digitalWrite(in2, LOW);
digitalWrite(in3, HIGH);
digitalWrite(in4, LOW);
}
void derecha() {
digitalWrite(in2, HIGH);
digitalWrite(in1, LOW);
digitalWrite(in4, HIGH);
digitalWrite(in3, LOW);
}
void adelante() {
digitalWrite(in1, HIGH);
digitalWrite(in2, LOW);
digitalWrite(in4, HIGH);
digitalWrite(in3, LOW);
}
void atras() {
digitalWrite(in2, HIGH);
digitalWrite(in1, LOW);
digitalWrite(in3, HIGH);
digitalWrite(in4, LOW);
} 


const int buzzerPin = 13;
const int flamePin = 11;
int Flame = LOW;

void setup() 
{
  pinMode(buzzerPin, OUTPUT);
  pinMode(flamePin, INPUT);
  Serial.begin(9600);
}

void loop() 
{
  Flame = digitalRead(flamePin);
  if (Flame== HIGH)
  {
    Serial.println("Fire!!!");
    digitalWrite(buzzerPin, HIGH);
  }
  else
  {
    Serial.println("No worries");
    digitalWrite(buzzerPin, LOW);
  }
}
