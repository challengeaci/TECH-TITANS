# TECH-TITANS

 // Initialising Pins of Stepper motor

#define A        2                     // the pin connected to the wire A of the coil A (or to the H-bridge pin controlling the same wire) 
#define A_bar    3                     // the pin connected to the wire A- of the coil A (or to the H-bridge pin controlling the same wire)
#define B        4                     // the pin connected to the wire B of the coil A (or to the H-bridge pin controlling the same wire)
#define B_bar    5                     // the pin connected to the wire B- of the coil A (or to the H-bridge pin controlling the same wire)
#define x        200              // smaller values may make the motor produce more speed and less torque
#define stepsPerRevolution 500        // you can the number of steps required to make a complete revolution in the data sheet of your motor
const int trigPin = 9;
const int echoPin = 10;
// defines variables
long duration;
int distance;
//Setting up modes of the above pins
void setup() {
  pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
  pinMode(echoPin, INPUT); // Sets the echoPin as an Input
  pinMode(6, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(A, OUTPUT);
  pinMode(A_bar, OUTPUT);
  pinMode(B, OUTPUT);
  pinMode(B_bar, OUTPUT);
  Serial.begin(9600); // Starts the serial communication
}

// Main Logic of the program
void loop() {  
  digitalWrite(trigPin, LOW);
delayMicroseconds(2);
// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);
// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);
// Calculating the distance
distance= duration*0.034/2;
// Prints the distance on the Serial Monitor

Serial.print("Distance: ");
Serial.println(distance);
  for (int i = 0; i < (stepsPerRevolution/4) ; i++) {
    digitalWrite(A, HIGH);
    digitalWrite(A_bar, LOW);
    digitalWrite(B, HIGH);
    digitalWrite(B_bar, LOW);
    delayMicroseconds (x);
    
    digitalWrite(A, LOW);
    digitalWrite(A_bar, HIGH);
    digitalWrite(B, HIGH);
    digitalWrite(B_bar, LOW);
    delayMicroseconds (x);

    digitalWrite(A, LOW);
    digitalWrite(A_bar, HIGH);
    digitalWrite(B, LOW);
    digitalWrite(B_bar, HIGH);
    delayMicroseconds (x);

    digitalWrite(A, HIGH);
    digitalWrite(A_bar, LOW);
    digitalWrite(B, LOW);
    digitalWrite(B_bar, HIGH);
    delayMicroseconds (x);

  }
  if(45<=distance<=55)
  {digitalWrite(A, LOW);
    digitalWrite(A_bar, LOW);
    digitalWrite(B, LOW);
    digitalWrite(B_bar, LOW);
  delay(10000);}
  else if(20<=distance<=30)
  {digitalWrite(A, LOW);
    digitalWrite(A_bar, LOW);
    digitalWrite(B, LOW);
    digitalWrite(B_bar, LOW);
    digitalWrite(6,1);
    digitalWrite(7,0);
    delay(10000);}
  else if (5<=distance<=10)
  {digitalWrite(A, LOW);
    digitalWrite(A_bar, LOW);
    digitalWrite(B, LOW);
    digitalWrite(B_bar, LOW);
  delay(10000);}
    
    
    
    
  
//   Counter Direction 
  for (int i = 0; i < (stepsPerRevolution/4); i++) {
    digitalWrite(A, HIGH);
    digitalWrite(A_bar, LOW);
    digitalWrite(B, LOW);
    digitalWrite(B_bar, HIGH);
    delayMicroseconds (x);

    digitalWrite(A, LOW);
    digitalWrite(A_bar, HIGH);
    digitalWrite(B, LOW);
    digitalWrite(B_bar, HIGH);
    delayMicroseconds (x);

    digitalWrite(A, LOW);
    digitalWrite(A_bar, HIGH);
    digitalWrite(B, HIGH);
    digitalWrite(B_bar, LOW);
    delayMicroseconds (x);

    digitalWrite(A, HIGH);
    digitalWrite(A_bar, LOW);
    digitalWrite(B, HIGH);
    digitalWrite(B_bar, LOW);
    delayMicroseconds (x);
  }
 
}
