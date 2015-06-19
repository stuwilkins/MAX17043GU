# MAX17043GU

MAX17043GU library for Arduino
>v1.0.0

Reads LiPo battery level and voltage using MAX17043GU.

Turned into a library from [Sparkfun's](https://www.sparkfun.com) example code for the [SparkFun LiPo Fuel Gauge](https://www.sparkfun.com/products/10617)

## Functions
Set up and set the I2C address  
`MAX17043GU(byte address)`

Set the percentage [0-32] for the low battery warning  
`MAX17043GU::config(byte percentage)`

Restart the calculations  
`restart()`

Get the voltage level (in steps op 1.25 mV)  
`voltageLevel()`

Get the battery level  
`fuelLevel()`

## Example
```
#include <MAX17043GU.h>

#define MAX17043_ADDRESS 0x36

float voltage;
float percentage;

MAX17043GU battery(MAX17043_ADDRESS);

void setup() 
{
	// Start serial
	Serial.begin(9600);
	// Start I2C
	Wire.begin();
	delay(100);
}

void loop() 
{
	// Get the values
	voltage = battery.voltageLevel();
	percentage = battery.fuelLevel();
	
	// Print
	Serial.print("Battery voltage: ");
	Serial.print(voltage, 2);
	Serial.println("V");
	Serial.print("Battery level");
	Serial.print(percentage, 2);
	Serial.println("%");
	
	// Wait
	delay(3000);
}
```

## Credits
All credits go to [Sparkfun](https://www.sparkfun.com).