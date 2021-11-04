# Engineering 2 Arduino
## Table of Contents

[Button Counter](https://github.com/zsiller38/Engineering2-Arduino/blob/main/README.md#button-with-counter)

[LED Fade](https://github.com/zsiller38/Engineering2-Arduino/blob/main/README.md#led-fade)

[Potentiometer](https://github.com/zsiller38/Engineering2-Arduino#potentiometer)

[Photoresistor](https://github.com/zsiller38/Engineering2-Arduino/blob/main/README.md#photoresistor)

### Button with Counter

#### Goal
>Make an led blink when I press a button and add a counter tracking the number of blinks. 

#### Code
```C++

// Zachary Siller
// Button Counter LED
// Press a button to make an LED start blinking. The LED will blink a maximum of ten times before turning off.

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
  buttonState = digitalRead(buttonPin);//If button is pressed continue to the other if statements. 
  Serial.print(buttonState);
  Serial.print("\t");
  if (buttonState == HIGH) {

    if (counter > 0 && counter < 11) {
      counter = counter + 1; //If counter is greater than 1 and less than 11, print the counter value.
      Serial.println(counter);//Add 1 to the counter value, and turn LED on and then off
      digitalWrite(2, HIGH);
      delay(250);
      digitalWrite(2, LOW);
      delay(250);
    }
    else if (counter == 10) {// If counter value equals 10, print done and turn LED off. 
      Serial.println("Done!");
      digitalWrite(buttonState, LOW);
    }
    else {
      
      digitalWrite(ledPin, LOW);// If neither of the pervious 2 apply turn LED off and print off. 
      Serial.println("Off!");
     
    }
  }
}


```
[Led button code link](https://create.arduino.cc/editor/zsiller38/3d4ac3cd-3ba6-4903-8081-033cfeda9844)

#### Wiring Diagram
<img src="https://user-images.githubusercontent.com/71402927/138759809-f91e0764-85c8-4371-8b0f-9eebf4d38dc9.png" alt="ButtonCounter" style="width:500px;">

#### Reflection
>The button with counter project was cool. It incorporated two projects we did last year, led button, and blink counter. I did have some trouble getting my LED to blink the correct number of times. It was just a problem with the numbers I put in as the number of times the LED would blink before stoping. I need to make sure I carefully read through my code because I made a lot of simple mistakes while writing the code.  

### LED Fade

#### Goal
>Make an led fade from off to on and back again using analog write.

#### Code
```C++
// Zachary Siller
// LED fade from bright to dark.
// Use a fade amount to adjust a brightness level and make an LED change brightness levels.


int led = 9;
int brightness = 0;
int fadeAmount = 5; //amount light value will increase or decrease by.

void setup() {
  pinMode(led, OUTPUT);
}


void loop() {

  analogWrite(led, brightness); //Tells LED to shine as bright as the brightness level.
  brightness = brightness + fadeAmount; //Adds fadeAmount to current brightnesslevel

  if (brightness <= 0 || brightness >= 255) {
    fadeAmount = -fadeAmount; //Allows for LED to get dimmer and decrease in light level.
  }
  delay(30);
}

```
[Led fade code link](https://create.arduino.cc/editor/zsiller38/b40ef046-296b-45ba-86f6-bbdcb434c180)

#### Wiring Diagram
<img src="https://github.com/zsiller38/Engineering2-Arduino/blob/main/images/ArduinoPhade.png?raw=true" alt="ArduinoFade" style="width:500px;">

#### Reflection
>The LED fade project was very easy and very short. Using analog write and then a fade amount to control how quickly the led will fade from on to off was quite enjoyable. It was a very easy project but a fun build-on to the led project we started in engineering 1. 

### Potentiometer

#### Goal
>Use a Potentiometer to manually adjust the brightness of an LED. 

#### Code
```C++

// Zachary Siller
// Control LED using a Potentiometer
// Use a potentiometer to change brightness of LED by turning potentiometer. 



const int analog_ip = A0;
const int LED = 5;
const int Servo = 10;
int inputVal = 0;
int brightness = 0;

void setup() {
  pinMode(LED, OUTPUT);
  Serial.begin(9600);
  
}

void loop() {
  inputVal = analogRead(analog_ip); // Reads potentiometer pin and says "inputVal" is equal to whatever it reads.
  Serial.println(inputVal); // Prints the "inputVal"
  brightness = map(inputVal,0,1023,255,0); // Potentiometer gives value 0-1023. Map turns that number into a number between 0-255. This becomes our LED brightness level. 
  
  analogWrite(LED, brightness); // Tells led what brightness to change to.
  delay(100);
}

```
[Potentiometer code link](https://create.arduino.cc/editor/zsiller38/09d12ddb-0646-4a83-91fe-912f266f885b)

#### Wiring Diagram
<img src="https://github.com/zsiller38/Engineering2-Arduino/blob/main/images/Potentiometer.png?raw=true" alt="Potentiometer" style="width:500px;">

#### Reflection
>I liked the potentiometer project. It was something I had never done before and I enjoyed using the serial monitor to print the brightness values, and see how they changed as I twisted the potentiometer. The code itself introduced some new ideas like using map to convert the range of the input value to a brightness level. 

### Photoresistor

#### Goal
>Use photoresistor to make an led turn on and off depending on the light value.

#### Code
```C++
// Zachary Siller
// Control LED using Photoresistor
// Use a photoresitor to turn and LED off if light level is high and off if light level is low. 


int light = 0; // store the current "light" value

void setup() {
  Serial.begin(9600);
  pinMode(8, OUTPUT);

}

void loop() {
  light = analogRead(A0);// Reads "light" level from photoresistor and prints it. 
  Serial.println(light);

  if (light > 600) {
    Serial.println("Light");//If the "light" level is greater then 600 turn the "light" off and print "light". 
    digitalWrite(8, LOW);
    delay(500);
  }
  else {
    Serial.println("Dark");// If "light" level less that 600 turn on "light" and print "dark". 
    digitalWrite(8, HIGH);

  }
  delay(1000);
}
```
[Photoresistor code link](https://create.arduino.cc/editor/zsiller38/c16c32f6-674d-4e8f-a83f-eee4dfbc34a6)

#### Wiring

<img src="https://user-images.githubusercontent.com/71402927/138344088-56e3a8ef-92a5-4b82-a249-19817e1891a0.png" alt="Photoresistor" style="width:500px;">

#### Reflection
>Once again this was a really fun project to look a the serial monitor on as the light value changed when you put your hand over the photoresistor. using the photoresistor to track the light value and then using if statements to tell the Arduino to turn the led on or off was fun but not too hard. 
