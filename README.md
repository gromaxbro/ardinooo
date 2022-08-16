
#define echoPin 9 // attach pin D2 Arduino to pin Echo of HC-SR04
#define trigPin 8 //attach pin D3 Arduino to pin Trig of HC-SR04

 
long duration; // variable for the duration of sound wave travel
int distance; // variable for the distance measurement

int i = 0;
int g = 2;
void setup()
{
  pinMode(trigPin, OUTPUT); // Sets the trigPin as an OUTPUT
  pinMode(echoPin, INPUT);
  pinMode(10, INPUT);
  pinMode(2, OUTPUT);
  pinMode(3, OUTPUT);
  pinMode(4, OUTPUT);
  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  Serial.begin(9600);

}

void loop()
{
  int r = digitalRead(10);
  if (r == 1){
    while(true){
      delayMicroseconds(2);
  // Sets the trigPin HIGH (ACTIVE) for 10 microseconds
    digitalWrite(trigPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(trigPin, LOW);
  // Reads the echoPin, returns the sound wave travel time in microseconds
    duration = pulseIn(echoPin, HIGH);
  // Calculating the distance
    distance = duration * 0.034 / 2; // Speed of sound wave divided by 2 (go and back)
  // Displays the distance on the Serial Monitor
    Serial.print("Distance: ");
    Serial.print(distance);
    Serial.println(" cm");
    if (distance > 6){
      digitalWrite(6, HIGH);
    
    }
    if (distance >11){
      digitalWrite(2, HIGH);
    }
    if (distance >43){
      digitalWrite(2, HIGH);
    }
    if (distance > 102 ){
      digitalWrite(3, HIGH);
    
    }
    if (distance > 167){
 
      digitalWrite(4, HIGH);
    
 
    }
    if (distance > 254){
 
      digitalWrite(5, HIGH);
    
 
    }
    else{
      digitalWrite(2, LOW);
      digitalWrite(3, LOW);
      digitalWrite(4, LOW);
      digitalWrite(5, LOW);
    }
    }
    
  }
  else{
    while(true){
      digitalWrite(g-1,LOW);
      digitalWrite(g,HIGH);
      delay(500);
      i++;
      g++;
      if(g == 8){
        g = 2;
      }
    }
  }
  
}

