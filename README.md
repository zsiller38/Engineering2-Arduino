# Engineering 2 Arduino
## Arduino Revisited
### LED Phade
#### Goal
>Make an led fade from off to on and back again using analog write.
#### Code
```int led = 9;
int brightness = 0;
int fadeAmount = 5;

void setup() {
  pinMode(led, OUTPUT);
}


void loop() {

  analogWrite(led, brightness);
  brightness = brightness + fadeAmount;

  if (brightness <= 0 || brightness >= 255) {
    fadeAmount = -fadeAmount;
  }
  delay(30);
}
```
#### Wiring Diagram
<img src="https://user-images.githubusercontent.com/71402927/133321916-7e90c5ee-e1fc-4543-a245-887f7ec27b36.png" alt="ArduinoFade" style="width:500px;">

#### Reflection
