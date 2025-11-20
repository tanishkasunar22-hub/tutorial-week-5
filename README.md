# tutorial-week-5
`Simulate a system with the specified resources as per the given circuit diagram and the source code in TinkerCad.`
### 1.	What is the difference between LM35 and TMP36 while interfacing with arduino?
```


```

### 2. Simulate SMART Sensor and Actuator
> Required Materials:
> - Arduino UNO
> - TMP36 sensor 
> - I2C LCD 
> - Conversion Logic
>   
> i.	Temperature (°C) = (VOUT – 500) / 10),  VOUT is in millivolts
>
> ii.	VOUT = reading from ADC * (5000 / 1023)

<img width="861" height="448" alt="image" src="https://github.com/user-attachments/assets/6ea9bb34-eea8-46e9-bea2-c938c27edbf3" />

Fig: Simulation Circuit Diagram






https://github.com/user-attachments/assets/e8a08b85-ef5e-49af-8ef4-9181254d9ef7


**Source Code: **
```
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);   // LCD address may be 0x27 or 0x3F

const int sensorPin = A3;  // TMP36 connected to A3

void setup() {
  lcd.init();              // Initialize LCD
  lcd.backlight();         // Turn on backlight
  lcd.setCursor(0, 0);     // first is character and second is line starting from 0
  lcd.print("TMP36 Sensor:");
  delay(500);
}

void loop() {
  int analogValue = analogRead(sensorPin);
  float voltage = analogValue * (5000 / 1023.0);   // Convert ADC to millivolts

  // TMP36: Temp(C) = (Vout - 500)/10
  float tempC = (voltage - 500) / 10.0;

  lcd.setCursor(0, 1);
  lcd.print("Temp: ");
  lcd.print(tempC, 1);     // 1 decimal place
  lcd.print(" C");

  delay(1000); // Wait for a second
}

```
### Learning Reflection
```

```
