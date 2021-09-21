# Engineering 2 Arduino
## Arduino Revisited
### LED Phade
#### Goal
>Make an led fade from off to on and back again using analog write.
#### Code
```C++

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
<img src="https://github.com/zsiller38/Engineering2-Arduino/blob/main/images/ArduinoPhade.png?raw=true" alt="ArduinoFade" style="width:500px;">

#### Reflection
>I thought this project was good.

### Button with Counter
#### Goal
>Make an led blink when I press a button and add a counter tracking the number of blinks. 
#### Code
```C++

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
<img src="(https://github.com/zsiller38/Engineering2-Arduino/blob/main/images/ButtonCounter.png)" alt="ButtonCounter" style="width:500px;">

#### Reflection
>I thought this project was good.

### Potentiometer
#### Goal
>Use a Potentiometer to manually ajust the brightness of an LED. 
#### Code
```C++

const int analog_ip = A0;
const int LED = 5;
const int Servo = 10
int inputVal = 0;
int brightness = 0;

void setup() {
  pinMode(LED, OUTPUT);
  Serial.begin(9600);
  
}

void loop() {
  inputVal = analogRead(analog_ip);
  Serial.println(inputVal);
  brightness = map(inputVal,0,1023,255,0);
  analogWrite(LED, brightness);
  delay(100);
}

```
#### Wiring Diagram

#### Reflection
