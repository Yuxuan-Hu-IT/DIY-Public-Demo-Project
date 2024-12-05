# DIY-Public-Demo-Project
DIY project description for IT 254

## The goal of this project is to build a Car parking sensor

### Software| Software                | Version          | Notes/Hidden Details |
|-------------------------|------------------|----------------------|
| Arduino IDE             | 1.8.13           | Latest stable release |
| Tinkercad               | N/A              | Used for circuit design  |


### Hardware
| Component               | Model/Version     | Notes/Hidden Details |
|-------------------------|-------------------|----------------------|
| Arduino Uno             | 1st Gen           | Make sure to use the correct board version in IDE |
| Ultrasonic Sensor       | HC-SR501          | Connect VCC to 5V, GND to GND, Trig to Pin 9, and Echo to Pin 10 |
| Buzzer                  | Passive buzzer    | Connect Positive (long leg) to Pin 12, Negative (short leg) to GND |
| Wires                   | N/A               | Make sure wires are working and properly connected |



*project code*


#define IN4  4
const int trigPin = 5;
const int echoPin = 6;
// define variables
long duration;
int distance = 0;
void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(4,OUTPUT);
  Serial.begin(9600);
}

void loop() {
  if ((distance <50) &&(distance > 0))
  {
    digitalWrite(IN4, HIGH);
  }
  else if ((distance > 51)&&(distance < 150))
  {
    digitalWrite(IN4, HIGH);
    delay(10*(distance-50));
    digitalWrite(IN4, LOW);
    delay(10*(distance-50));
  }
  else if ((distance > 151)&&(distance < 200)) {
    digitalWrite(IN4, HIGH);
    delay(1000);
    digitalWrite(IN4, LOW);
    delay(1000);
  }
  else if (distance > 200){
    digitalWrite(IN4, LOW);
  }
  delayMicrosecond(10);
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  degitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distance = duration*0.034/2;
  Serial.print("Distance: ");
  Serial.println(distance);
}
