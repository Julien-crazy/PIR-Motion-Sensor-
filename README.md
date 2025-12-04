# PIR-Motion-Sensor-
1. The PIR Motion Sensor used in this assignment functions by detecting motion based on changes in infrared changes. This kind of motion sensor is used today for many security purposes in businesses and home grounds.
2. In this miniture project I used a PIR mottion sensor in which a LED begins to start blinking when motion is detected. The project worked very smoothly and even turns off when motion isn't detected. Though, there is a slight delay when it starts/stops blinking due to the adjusting change in infrared.






   HERE IS A CODE EXAMPLE OF THE PIR MOTION SENSOR IN EFFECT

   
// Define the pins for the LED and PIR sensor
const int ledPin = 13;    // Digital pin for the LED
const int pirPin = 2;     // Digital pin for the PIR sensor

// Variable to store the state of the PIR sensor
int pirState = LOW;       // Assume no motion initially
int val = 0;              // Variable to read the sensor's value

void setup() {
  // Initialize the LED pin as an output
  pinMode(ledPin, OUTPUT);
  // Initialize the PIR sensor pin as an input
  pinMode(pirPin, INPUT);

  // Start serial communication for debugging (optional)
  Serial.begin(9600);
  Serial.println("PIR Sensor with LED initialized.");
  Serial.println("Waiting for PIR sensor to calibrate (approx. 30-60 seconds)...");

  // Optional: Blink LED during PIR sensor calibration
  for (int i = 0; i < 5; i++) {
    digitalWrite(ledPin, HIGH);
    delay(500);
    digitalWrite(ledPin, LOW);
    delay(500);
  }
  Serial.println("PIR sensor calibrated. Ready for motion detection.");
}

void loop() {
  // Read the value from the PIR sensor
  val = digitalRead(pirPin);

  // Check if motion is detected (PIR sensor output is HIGH)
  if (val == HIGH) {
    digitalWrite(ledPin, HIGH); // Turn LED ON

    // If the PIR state was previously LOW, it means motion has just been detected
    if (pirState == LOW) {
      Serial.println("Motion detected!");
      pirState = HIGH; // Update the PIR state
    }
  } else {
    digitalWrite(ledPin, LOW); // Turn LED OFF

    // If the PIR state was previously HIGH, it means motion has just ended
    if (pirState == HIGH) {
      Serial.println("Motion ended!");
      pirState = LOW; // Update the PIR state
    }
  }
  delay(100); // Small delay to prevent rapid readings
}


HERE IS A VIDEO EXAMPLE
https://github.com/user-attachments/assets/c6e913b8-967f-48f1-bb0b-eb8b51b25df3


