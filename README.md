# Task2-Motion-of-4-servo-motors-
Arduino program to control four servo motors using the Sweep example. The servos run for 2 seconds, then hold at 90 degrees.

the code :
#include <Servo.h>

Servo servo1;
Servo servo2;
Servo servo3;
Servo servo4;

int pos = 0;
bool finished = false;

void setup() {
  servo1.attach(6);
  servo2.attach(9);
  servo3.attach(10);
  servo4.attach(11);
}

void loop() {
  if (finished == false) {
    unsigned long startTime = millis();
    while (millis() - startTime < 2000) {
      for (pos = 0; pos <= 180 && millis() - startTime < 2000; pos += 1) {
        servo1.write(pos);
        servo2.write(pos);
        servo3.write(pos);
        servo4.write(pos);
        delay(15);
      }
      for (pos = 180; pos >= 0 && millis() - startTime < 2000; pos -= 1) {
        servo1.write(pos);
        servo2.write(pos);
        servo3.write(pos);
        servo4.write(pos);
        delay(15);
      }
    }
    // Hold all motors at 90 degrees
    servo1.write(90);
    servo2.write(90);
    servo3.write(90);
    servo4.write(90);

    finished = true;
  }
}
