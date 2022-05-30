# High School Day 2: Programmable Electronics Workshop

## *Goal: Foster interest in participants to explore topics in the field of Electronics.*

## Learning Objectives

- Introduce Students to topics in Electronics and general Circuit-Building concepts
- Introduce Students to basic Arduino Microcontroller programming and how such devices can be used to create programmatic and functional systems
- Teach Students how various electronics components function and how they can be used to build circuits

## Resources and Materials

> **Note:** If attempting to use this specific module as a template for running a similar workshop, it is recommended that one checks component sources for prebuilt kits within the group's budget and structure the session around the parts available in the purchased kits, as prebuilt kits tend to be significantly less expensive than purchasing individual components separately, but can vary in terms of included contents with time. Furthermore, utilizing kits fundamentally decreases the amount of time needed to order, organize, and otherwise prepare materials for such activities.

[//]: # (TODO)

- Arduino kit
  - Arduino Uno
  - LED
- Computers running Arduino IDE
- Paper
- Writing Utensils (Pencils)

## Setup

1. Install the Arduino IDE on all Student computers
    - Test for a successful "Blink" program upload from all of the Computers
2. Test that all computers are able to access <https://edukits.co/code/>
3. Ensure that there are enough kits for all participants, with additional spare kits equivalent to roughly 10% of the kits required.

## Projects Overview

1. [Serial Monitor Hello World](#project-1-serial-monitor-hello-worldhttpsarduinogetstartedcomtutorialsarduino-hello-world)
2. [Builtin LED Blink](#project-2-builtin-led-blinkhttpswwwarduinoccentutorialbuiltinexamplesblink)
3. [External LED](#project-3-external-led-blinkhttpswwwarduinoccentutorialbuiltinexamplesblink)
4. [Button-Toggle LED](#project-4-button-toggle-ledhttpsarduinogetstartedcomtutorialsarduino-button-toggle-led)
5. [Multiple External LED](#project-5-multiple-external-led)
6. [Multiple LED Blink](#project-6-multiple-led-blink)

### `Time-permitting Challenges`

1. [Arduino LED Dice](#challenge-1-arduino-led-dicehttpscreatearduinoccprojecthubevdsled-dice-885cf1)
2. [Binary Counter](#challenge-2-binary-counterhttpscreatearduinoccprojecthubmadhurbajpaibinary-counter-using-leds-2089d9)

## Agenda

---

1. Briefly review the definition of a computer.
    > A computer is a machine or device that performs processes, calculations and operations based on instructions provided by a software or hardware program. It has the ability to accept data (input), process it, and then produce outputs.
    > <div style="text-align: right"> - Technopedia </div>

2. Explain what microcontrollers are and how the can be used to program electronic devices.

3. Introduce the Arduino Uno, a type of microcontroller built to be easy to set up and program through the Arduino IDE.

4. Guide students through connecting an Arduino Uno to the computer and setting up the IDE to be able to program the Arduino Uno.

5. Introduce the Serial Monitor, an easy way to receive text feedback from the microcontroller.

---

### [**Project 1: Serial Monitor Hello World**](https://arduinogetstarted.com/tutorials/arduino-hello-world)

```cpp
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600); // Open a serial connection that communicates at 9600 bits per second
  Serial.println("Hello World!"); // Print "Hello World" (without the quotes) to the serial monitor
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

---

6. Introduce the built-in LED, which can be controlled by changing the voltage of the builtin LED pin on the Arduino Uno.

---

### [**Project 2: Builtin LED Blink**](https://www.arduino.cc/en/Tutorial/BuiltInExamples/Blink)

```cpp
// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  Serial.begin(9600);
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  Serial.println("ON");
  delay(1000);                       // wait for 1000 milliseconds (1 second)
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
  Serial.println("OFF");
  delay(1000);                       // wait for 1000 milliseconds (1 second)
}
```

---

7. Introduce external LEDs (with resistors) and show how they can be powered by the Arduino's VCC pin.
    - Warn of the dangers of using LEDs without a resistor. (Demonstrate?)
8. Explain GPIO pins and how they can be used as an output to programmatically control voltage along a wire.

---

### [**Project 3: External LED Blink**](https://www.arduino.cc/en/Tutorial/BuiltInExamples/Blink)

#### P3 Schematic

![Schematic of LED Blink Circuit](image/hsd2_lessonPlan/1653837032396.png)

#### P3 Wiring Diagram

![Wiring Diagram of LED Blink Circuit](image/hsd2_lessonPlan/1653837089888.png)

```cpp
// define the GPIO pin the external LED is connected to
#define LED_PIN 12

// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin LED_PIN as an output.
  pinMode(LED_PIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_PIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for 1000 milliseconds (1 second)
  digitalWrite(LED_PIN, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);                       // wait for 1000 milliseconds (1 second)
}
```

9. Introduce push-button switches and how they can be used to close a circuit so that current can flow through it.

10. Explain how GPIO pins can be used as an input to detect changes in the voltage on its pins.
    - Also mention that pinMode INPUT_PULLUP should be used instead of regular INPUT because you would otherwise have random input readings while the button is not pressed down.
    - If someone asks for more information, mention that you can explain it in more detail if there is time after the end of class. [Helpful resource](https://roboticsbackend.com/arduino-input_pullup-pinmode/)

---

### [**Project 4: Button-Toggle LED**](https://arduinogetstarted.com/tutorials/arduino-button-toggle-led)

```cpp
#define LED_PIN 12
#define BUTTON_PIN 7 // Arduino pin connected to button's pin

// Variables that will change:
int ledState = LOW;     // the current state of LED
int lastButtonState;    // the previous state of button
int currentButtonState; // the current state of button

void setup() {
  Serial.begin(9600);                // initialize serial
  pinMode(BUTTON_PIN, INPUT_PULLUP); // set arduino pin to input pull-up mode
  pinMode(LED_PIN, OUTPUT);          // set arduino pin to output mode

  currentButtonState = digitalRead(BUTTON_PIN);
}

void loop() {
  lastButtonState    = currentButtonState;      // save the last state
  currentButtonState = digitalRead(BUTTON_PIN); // read new state

  if(lastButtonState == HIGH && currentButtonState == LOW) {
    Serial.println("The button is pressed");

    // toggle state of LED
    ledState = !ledState;

    // control LED according to the toggled state
    digitalWrite(LED_PIN, ledState); 
  }
}
```

11. Explain how multiple external LEDs can be used at once by simply defining multiple GPIO pins and repeating the digitalWrite code as needed with those new pins.

---

### **Project 5: Multiple External LED**

> TODO: Code, Schematics, and Wiring Diagram

#### P5 Wiring Diagram

---

### **Project 6: Multiple LED Blink**

Same Schematic and Wiring as [Project 5](#project-5-multiple-external-led)

```cpp
// Note: This code was written to be as useful to participants as possible for debugging, under the assumption that participants do not yet know about topics such as arrays or functions. As such, please excuse the immense redundancy this code example displays.

// Initialize the LED Pins on Pins 2-7 (Since pins 0 and 1 are reserved for the USB communication with the computer and cannot be used for this purpose)
#define LED_PIN_1 2
#define LED_PIN_2 3
#define LED_PIN_3 4
#define LED_PIN_4 5
#define LED_PIN_5 6
#define LED_PIN_6 7

// the setup function runs once when you press reset or power the board
void setup() {
  Serial.begin(9600);
  // initialize the digital pins as outputs.
  pinMode(LED_PIN_1, OUTPUT);
  pinMode(LED_PIN_2, OUTPUT);
  pinMode(LED_PIN_3, OUTPUT);
  pinMode(LED_PIN_4, OUTPUT);
  pinMode(LED_PIN_5, OUTPUT);
  pinMode(LED_PIN_6, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_PIN_1, HIGH);   // turn the LED on (HIGH is the voltage level)
  Serial.println("1 ON");
  delay(1000);                       // wait for 1000 milliseconds (1 second)
  digitalWrite(LED_PIN_1, LOW);    // turn the LED off by making the voltage LOW
  Serial.println("1 OFF");
  delay(1000);                       // wait for 1000 milliseconds (1 second)

  digitalWrite(LED_PIN_2, HIGH);   // turn the LED on (HIGH is the voltage level)
  Serial.println("2 ON");
  delay(1000);                       // wait for 1000 milliseconds (1 second)
  digitalWrite(LED_PIN_2, LOW);    // turn the LED off by making the voltage LOW
  Serial.println("2 OFF");
  delay(1000);

  digitalWrite(LED_PIN_3, HIGH);   // turn the LED on (HIGH is the voltage level)
  Serial.println("3 ON");
  delay(1000);                       // wait for 1000 milliseconds (1 second)
  digitalWrite(LED_PIN_3, LOW);    // turn the LED off by making the voltage LOW
  Serial.println("3 OFF");
  delay(1000);  

  digitalWrite(LED_PIN_4, HIGH);   // turn the LED on (HIGH is the voltage level)
  Serial.println("4 ON");
  delay(1000);                       // wait for 1000 milliseconds (1 second)
  digitalWrite(LED_PIN_4, LOW);    // turn the LED off by making the voltage LOW
  Serial.println("4 OFF");
  delay(1000); 

  digitalWrite(LED_PIN_5, HIGH);   // turn the LED on (HIGH is the voltage level)
  Serial.println("5 ON");
  delay(1000);                       // wait for 1000 milliseconds (1 second)
  digitalWrite(LED_PIN_5, LOW);    // turn the LED off by making the voltage LOW
  Serial.println("5 OFF");
  delay(1000);         

  digitalWrite(LED_PIN_6, HIGH);   // turn the LED on (HIGH is the voltage level)
  Serial.println("6 ON");
  delay(1000);                       // wait for 1000 milliseconds (1 second)
  digitalWrite(LED_PIN_6, LOW);    // turn the LED off by making the voltage LOW
  Serial.println("6 OFF");
  delay(1000);   
}
```

---
---

> ### The following are bonus challenges ideas that students can attempt to design and build with the knowledge they have previously accumulated during the workshop.

#### Click on the Challenge Headers to be taken to a brief description of these projects.

##### There are hundreds of ways one could go about implementing each of these challenges, but included below are my renditions of them. I thoroughly expect the participants of this workshop to produce unique versions compared to the ones that are provided here, though the code included here can be helpful to provide hints or otherwise help students debug should they become stuck.

---

### [**Challenge 1: Arduino LED Dice**](https://create.arduino.cc/projecthub/EvdS/led-dice-885cf1)

#### TODO: include my own code and circuit diagram for LED Dice

#### C1 uses the same Schematic and Circuit Diagram as [Project 5](#project-5-multiple-external-led)

---

### [**Challenge 2: Binary Counter**](https://create.arduino.cc/projecthub/Madhur_Bajpai/binary-counter-using-leds-2089d9)

#### TODO: include my own code and circuit diagram for Binary Counter

#### C2 uses the same Schematic and Circuit Diagram as [Project 5](#project-5-multiple-external-led)

---

Note: The original sources of public-domain code or project ideas that have been used have been linked to in the headers of the sections that they appear in. Additionally, all original code in this document is hereby permitted to be used as public-domain code under the Public-domain-equivalent license.
