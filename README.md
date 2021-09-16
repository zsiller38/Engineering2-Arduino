# Engineering 2 Arduino
## Arduino Revisited
### LED Phade
#### Goal
>Make an led fade from off to on and back again using analog write.
#### Code
```C++
/*
int led = 9;
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
>I thought this project was good.

### Button with Counter
#### Goal
>Make an led blink when I press a button and add a counter tracking the number of blinks. 
#### Code
```C++
*/

int ledPin = 2;
int buttonPin = 13;
int buttonState = LOW;
int counter = 1;

void setup() {
  Serial.begin(9600);
  pinMode(ledPin, OUTPUT);
  pinMode(buttonPin, INPUT);

}


void loop() {
  buttonState = digitalRead(buttonPin);
  Serial.print(buttonState);
  Serial.print("\t");
  if (buttonState == HIGH) {

    if (counter > 0 && counter < 11) {
      counter = counter + 1;
      Serial.println(counter);
      digitalWrite(2, HIGH);
      delay(250);
      digitalWrite(2, LOW);
      delay(250);
    }
    else if (counter == 10) {
      Serial.println("Done!");
      digitalWrite(buttonState, LOW);
    }
    else {
      
      digitalWrite(ledPin, LOW);
      Serial.println("Off!");
     
    }
  }
}

```
#### Wiring Diagram
<img src="https://user-images.githubusercontent.com/71402927/133321916-7e90c5ee-e1fc-4543-a245-887f7ec27b36.png" alt="ArduinoFade" style="width:500px;">

#### Reflection
>I thought this project was good.
