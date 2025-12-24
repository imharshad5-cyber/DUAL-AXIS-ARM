# DUAL-AXIS-ARM
This application provides a simple yet effective method for controlling servo motors using a joystick, making it suitable for robotics learning, academic projects, and motion-control experiments. The design emphasizes real-time responsiveness, ease of control, and bio-inspired robotic movement.

#include <Servo.h>

// Create servo objects
Servo myServo1;
Servo myServo2;

// Servo PWM pins
int servo1 = 3;
int servo2 = 5;

// Joystick analog pins
int joyX = A0;
int joyY = A1;

void setup() {
  myServo1.attach(servo1);
  myServo2.attach(servo2);
}

void loop() {
  // Read joystick values (0–1023)
  int valX = analogRead(joyX);
  int valY = analogRead(joyY);

  // Map joystick values to servo angle (10°–170°)
  valX = map(valX, 0, 1023, 10, 170);
  valY = map(valY, 0, 1023, 10, 170);

  // Move servos
  myServo1.write(valX);
  myServo2.write(valY);

  delay(5);
}
