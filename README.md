Title: Automated-Lighting-Control-System

Problem Statement: In many classrooms, homes, and offices, lights are often left ON even when the room is empty or when sufficient natural daylight is available. This leads to unnecessary electricity wastage and increased power bills. Manual control of lighting systems is inefficient and unreliable.

Purpose / Objective: The purpose of this project is to save electrical energy by automatically controlling lights based on room occupancy and ambient light conditions. The system ensures that lights are turned ON only when the room is occupied and dark, and turned OFF when not needed.

Solution Approach / How it Works:
*The system uses a motion sensor to detect if someone enters or leaves a room and a light sensor to measure ambient brightness.
*If the room is dark and someone enters, the lights turn on automatically.
*If the room is bright, the lights remain off, even if someone enters.
*When no movement is detected for a set time, the lights turn off.
*This ensures lights are only on when needed, avoiding unnecessary energy usage.

Components Used:
*ESP32 Microcontroller – Acts as the main control unit, processes sensor data, and controls the lighting system. It also supports Wi-Fi for future IoT integration.
*LDR (Light Dependent Resistor) – Measures room light intensity to determine whether the room is bright or dark.
*PIR Sensor – Detects human movement to identify room occupancy.
*LED Lights – Act as the output load and are controlled automatically by the system.


Energy Saving Calculation : To calculate energy savings, the classroom timetable was analyzed to identify actual usage hours. Light intensity was measured at different times of the day using the LDR sensor. During periods with sufficient daylight or when the classroom was unoccupied, the system kept the lights OFF. Based on this data, the amount of electrical energy saved by avoiding unnecessary lighting was calculated.

Results:
*Significant reduction in electricity wastage
*Automatic lighting based on occupancy and brightness
*Lower electricity consumption and power bills
*Improved energy efficiency and user convenience

Applications:
*Classrooms and educational institutions
*Homes and offices
*Smart buildings
*Energy-efficient lighting systems

Key Skills Used:
*ESP32 / Microcontroller Programming
*PIR and LDR Sensor Interfacing
*Energy Management and Automation

CODE:
int pirSensorPin = 12;
int ledPin = 14;
int ldrPin = 34; // Analog pin for LDR on ESP32

int ldrThreshold = 2000; // Adjust this threshold based on ambient light level

void setup() {
  pinMode(pirSensorPin, INPUT);
  pinMode(ledPin, OUTPUT);
  Serial.begin(115200); // Baud rate for ESP32
}

void loop() {
  int pirValue = digitalRead(pirSensorPin);
  int ldrValue = analogRead(ldrPin);

  Serial.print("LDR Value: ");
  Serial.println(ldrValue);

  if (ldrValue > ldrThreshold) { // It's bright enough
    if (pirValue == HIGH) {
      digitalWrite(ledPin, HIGH);
      Serial.println("Motion detected and bright → LED ON");
    } else {
      digitalWrite(ledPin, LOW);
      Serial.println("No motion → LED OFF");
    }
  } else {
    digitalWrite(ledPin, LOW);
    Serial.println("Too bright → LED OFF");
  }

  del
