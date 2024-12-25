#include "DHT.h"

// Define pins for DHT11 sensor and motors
#define DHTPIN 4       // DHT11 data pin connected to digital pin 4
#define DHTTYPE DHT11  // Define sensor type as DHT11

#define MOTOR1_IN1 8   // Motor 1 input pin 1
#define MOTOR1_IN2 9   // Motor 1 input pin 2
#define MOTOR2_IN1 10  // Motor 2 input pin 1
#define MOTOR2_IN2 11  // Motor 2 input pin 2

#define LDR_PIN A1     // Analog pin connected to LDR
#define LED_PIN 6      // Digital pin connected to LED
#define THRESHOLD 500  // Light intensity threshold value

DHT dht(DHTPIN, DHTTYPE);  // Initialize DHT sensor


void setup() {
  Serial.begin(9600);  // Start serial communication at 9600 baud rate
  dht.begin();         // Initialize the DHT sensor

  // Set motor pins as outputs
  pinMode(MOTOR1_IN1, OUTPUT);
  pinMode(MOTOR1_IN2, OUTPUT);
  pinMode(MOTOR2_IN1, OUTPUT);
  pinMode(MOTOR2_IN2, OUTPUT);

  pinMode(LED_PIN, OUTPUT);  // Set LED pin as output
}

void loop() {
  delay(2000);  // Wait for sensor to stabilize (DHT11 has a sampling rate of once per second)

  // Read temperature and humidity from the DHT11 sensor
  int ldrValue = analogRead(LDR_PIN);  // Read LDR value
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();

  Serial.print("LDR Value: ");
  Serial.println(ldrValue);  // Print LDR value to Serial Monitor

  // Check if readings are valid
  if (isnan(temperature) || isnan(humidity)) {
    Serial.println("Failed to read from DHT sensor!");
    Serial.println("Check your Sensors and Connections");

    //return;
  }

  else {
    Serial.print("Temperature: ");
    Serial.print(temperature);
    Serial.println(" C");

    Serial.print("Humidity: ");
    Serial.print(humidity);
    Serial.println(" %");

    // Control Motor 1 based on temperature > 40°C
    if (temperature >= 40) {
      digitalWrite(MOTOR1_IN1, HIGH);  // Turn Motor 1 ON (forward rotation)
      digitalWrite(MOTOR1_IN2, LOW);
      Serial.println("Fan ON");
    } else {
      digitalWrite(MOTOR1_IN1, LOW);  // Turn Motor OFF
      digitalWrite(MOTOR1_IN2, LOW);
      Serial.println("Fan OFF");
    }

    // Control Motor 2 based on humidity > 60%
    if (humidity >= 60) {
      digitalWrite(MOTOR2_IN1, HIGH);  // Turn Motor B ON (forward rotation)
      digitalWrite(MOTOR2_IN2, LOW);
      Serial.println("Hum. Controller ON");
    } else {
      digitalWrite(MOTOR2_IN1, LOW);  // Turn Motor OFF
      digitalWrite(MOTOR2_IN2, LOW);
      Serial.println("Hum. Controller OFF");
    }
  }

  // Print temperature and humidity values to the Serial Monitor



  if (ldrValue < THRESHOLD) {     // If light intensity is low
    digitalWrite(LED_PIN, HIGH);  // Turn ON LED
    Serial.println("LED ON");
  } else {                       // If light intensity is high
    digitalWrite(LED_PIN, LOW);  // Turn OFF LED
    Serial.println("LED OFF");
  }
}
