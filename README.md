# Engineering 2 Arduino
## Table of Contents
[LED Fade](https://github.com/zsiller38/Engineering2-Arduino/blob/main/README.md#led-fade)

[Button Counter](https://github.com/zsiller38/Engineering2-Arduino/blob/main/README.md#button-with-counter)

[Potentiometer](https://github.com/zsiller38/Engineering2-Arduino#potentiometer)

[Photoresistor](https://github.com/zsiller38/Engineering2-Arduino/blob/main/README.md#photoresitor)

### LED Fade
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
>The LED fade project was very easy and very short. Using analog write and then a fade amount to control how quickly the led will fade from on to off was quite enjoyable. It was avery easy project but a fun build on to the led project we started with in engineering 1. 

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
<img src="https://github.com/zsiller38/Engineering2-Arduino/blob/main/images/ButtonCounter.png?raw=true" alt="ButtonCounter" style="width:500px;">

#### Reflection
>The project was interesting because we intoduced some new elements like analog write. It was very simaler to the counter led we did last year, so it was not that hard. I did have some trouble with getting the led to stop anfter the correct number of blink, but by changing the counter starting value I eventually got it. 

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
<img src="https://github.com/zsiller38/Engineering2-Arduino/blob/main/images/Potentiometer.png?raw=true" alt="Potentiometer" style="width:500px;">

#### Reflection

### Photoresistor
#### Goal
#### Code
```C++
int light = 0; // store the current light value

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  pinMode(8, OUTPUT);

}

void loop() {
  // put your main code here, to run repeatedly:
  light = analogRead(A0);
  Serial.println(light);

  if (light > 600) {
    Serial.println("Light");
    digitalWrite(8, LOW);
    delay(500);
  }
  else {
    Serial.println("Dark");
    digitalWrite(8, HIGH);

  }
  delay(1000);
}

```
#### Wiring
![photoresistor](https://user-images.githubusercontent.com/71402927/138344088-56e3a8ef-92a5-4b82-a249-19817e1891a0.png | width=500)

#### Reflection
