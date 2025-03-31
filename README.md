#include <Wire.h>
#include <PCF8574.h>

// Create PCF8574 instances for two I/O expanders
PCF8574 pcf1(0x20); // Address of the first PCF8574
PCF8574 pcf2(0x21); // Address of the second PCF8574

void setup() {
  Wire.begin(); // Initialize the I2C communication

  // Initialize the PCF8574 I/O expanders
  pcf1.begin();
  pcf2.begin();

  // Set initial states for pin 3 and pin 5 on both expanders
  pcf1.write(3, LOW);
  pcf1.write(5, LOW);
  pcf1.write(6, LOW);
  pcf2.write(3, LOW);
  pcf2.write(5, LOW);
  pcf2.write(6, LOW);
}

void loop() {
  // Toggle LEDs on pin 3 and pin 5 on the first expander
  pcf1.write(3, HIGH);
  pcf2.write(6, HIGH);
  delay (7000);
  pcf1.write(3, LOW);
  pcf1.write(5, HIGH);
  delay(1000); // Wait for 500 milliseconds
  //pcf1.write(3, LOW);
  pcf1.write(5, LOW);
  pcf1.write(6, HIGH);
  pcf2.write(6, LOW);

  pcf2.write(3, HIGH);
  delay (7000);

 
  pcf2.write(3, LOW);
  
   pcf2.write(5, HIGH);
   delay (1000);
  pcf2.write(5, LOW);

 pcf2.write(6, HIGH);
  pcf1.write(6, LOW);

