#include <Stepper.h>

// Define Constants
#define MOTOR_PIN_1 13
#define MOTOR_PIN_2 12
#define MOTOR_PIN_3 14
#define MOTOR_PIN_4 27
#define X_PIN 34
#define POT_PIN 26

// Number of steps per internal motor revolution 
const float STEPS_PER_REV = 100;

// Create Instance of Stepper Class
Stepper steppermotor(STEPS_PER_REV, MOTOR_PIN_1, MOTOR_PIN_3, MOTOR_PIN_2, MOTOR_PIN_4);

void setup() {
  // Set up Serial communication if needed
  Serial.begin(9600);
}

void loop() {
  // Read the potentiometer value
  int sensorValue = analogRead(POT_PIN);
  
  // Calculate gear reduction dynamically based on potentiometer value
  const float GEAR_RED = sensorValue / 20.5;

  // Number of steps per internal motor revolution 
const float STEPS_PER_REV = sensorValue / 20.5;
  
  // Number of steps per geared output rotation
  const float STEPS_PER_OUT_REV = STEPS_PER_REV * GEAR_RED;

  // Read joystick value
  int joystickValue = analogRead(X_PIN);

  if (joystickValue > 2000 && joystickValue < 2387) {
    // Do nothing or perform any other action when joystick is in the middle position
  }
  else if (joystickValue < 2000) {
    // Move the stepper motor counterclockwise
    steppermotor.setSpeed(STEPS_PER_REV);  // Adjust speed as needed
    steppermotor.step(-30);
  }
  else if (joystickValue == 4095) {
    // Move the stepper motor clockwise
    steppermotor.setSpeed(STEPS_PER_REV);  // Adjust speed as needed
    steppermotor.step(30);
  }

  // Optionally print sensor and joystick values for debugging
  Serial.print("Sensor Value: ");
  Serial.print(sensorValue);
  Serial.print(", Joystick Value: ");
  Serial.println(joystickValue);

  delay(10);  // Add a small delay to avoid rapid changes
}
