---
hidden: true
---

# Embeded Programing

1. Learning the basic of computer
2. Setting up Auduino
3. code example

```cpp
void setup() {
 Serial.begin(115200);
 Serial.println("Hello, world!");

}

void loop() {
 tone(40,400,600);
 delay(800);
 tone(46,400,600);
 delay(800);
 tone(46,440,600);
 delay(800);

 tone(40,400,600);
 delay(800);
 tone(46,400,600);
 delay(800);
 tone(46,440,600);
 delay(800);

 tone(40,400,600);
 delay(800);
 tone(46,400,600);
 delay(800);
 tone(46,440,600);
 delay(800);

}

```

4. Connect buzzer to Arduino Board

Ground-negative, pin-positive

Board pinout:

{% embed url="https://fablabbcn-projects.gitlab.io/electronics/barduino-docs/GettingStarted/pinout/" %}

<figure><img src="../.gitbook/assets/Screenshot 2026-02-12 120147.png" alt=""><figcaption></figcaption></figure>

The Barduino board uses an ESP32-S microcontroller (ESP32-S3) as its main CPU.

Baarduino is a development board, which is a ready-to-use circuit board that contains a microcontroller plus all the supporting components needed to program and test it easily.

It is made to help us develop, test, and prototype electronic projects without building a circuit from scratch.

**Digital** **Input**: GPIO 01-21

**Touch and Capacitive inputs:** Touch01-07

**Temperature sensor**: GPIO 08-09

**Output**: GPIO 48 (LED), GPIO 46 (Buzzer), GPIO38 (Neopixel)

The Pinout shows where the power goes, what function does each pin has, and organize all the functions on the board.

The purpose of these pins is **Digital I/O**- to digital read button, **Analog input (ADC)**-read sensors that output analog voltages, **PWM output**- dim LEDs, control motor speed

Arduino IDE is a code editor that help us to code a microcontroller within its function and connect any outer inputs and outputs and program them.

5. How to read the voltage on a bit

add LED to arduino: long leg-positive

connect resistor to LED

\`electricity flow from high(positive) to low(negative)

```cpp
void setup() {
 Serial.begin(115200);
 Serial.println("Hello, world!");

 pinMode(2,OUTPUT);

}

void loop() {
 
 digitalWrite(2,HIGH);

 delay(400);
 Serial.println("Hey!");
 delay(400);
 Serial.println("Zeeee!");
 tone(50,440,500);
}

```

<figure><img src="../.gitbook/assets/Screenshot 2026-02-12 122506.png" alt=""><figcaption></figcaption></figure>

6. exercise: Turn on the programmable LED on Barduino (pin 48), ON for the "S"s, OFF for the "O"s

```cpp
void setup() {
 Serial.begin(115200);
 Serial.println("Hello, world!");

 pinMode(48,OUTPUT);

}

void loop() {
 
 digitalWrite(48,HIGH);
 //digitalWrite(48,100);
 Serial.println("S");

 tone(46,400,600);
 delay(800);
 tone(46,400,600);
 delay(800);
 tone(46,400,600);
 delay(800);

 digitalWrite(48,LOW);
 Serial.println("O");

 tone(46,440,200);
 delay(400);
 tone(46,440,200);
 delay(400);
 tone(46,440,200);
 delay(400);

 digitalWrite(48,HIGH);
 //digitalWrite(48,100);
 Serial.println("S");

 tone(46,400,600);
 delay(800);
 tone(46,400,600);
 delay(800);
 tone(46,400,600);
 delay(800);

 delay (800);

}

```

***

## Individual assignment

* Write and test a program for an embedded system using a microcontroller to interact (with local input &/or output devices) and communicate (with remote wired or wireless connections)

#### ESP32 Datasheet

{% embed url="https://documentation.espressif.com/esp32-s3_datasheet_en.pdf" %}

I learned how the pins on ESP32 is distributed to different pins on the barduino itself so that it can be connected to outer input and outputs. There is the information of the layouts and functions of all the pins, including the voltage, current ratings.

After reading the datasheet, I have a better understanding of how each pin function and connect within each other, I think it is a good fundation for electronic design.

#### Interact with ESP32 , touch the board and make it blink and sing

First, I needed to understand what a touch sensor is in ESP32.

> Touch sensor is a peripheral, that has an internal oscillator circuit and it measures charge/discharge frequency over a fixed period of time on respective GPIO pins. Therefore these touch sensors are also known as capacitive sensors.

The conductivity in human body will change the RC circuit that is attached to the touch sensor.

I did research online and learned about the touch sensor.

touchRead() counts the number of charge/discharge cycles.&#x20;

Then, I pulled out an example code in the ESP32 Library located in IDE Arduino to learn about how to test a touch sensor. Becasue at first I thought I could use the HIGH/LOW in touchRead() to determine whether the sensor is on or not. However, through the test touch sensor example, I learned that the read number is a huge range of numbers, to be able to turning touch sensor "ON" and "OFF" in order to control LED and sound, I need to use if() value.

```cpp


#include "Arduino.h"

int threshold = 1500;  
bool touch1detected = false;

void gotTouch1() {
  touch1detected = true;
}


void setup() {
  Serial.begin(115200);
  delay(1000);  

  Serial.println("\n ESP32 Touch Interrupt Test\n");
  touchAttachInterrupt(T7, gotTouch1, threshold);

  pinMode(48,OUTPUT);
}

void loop() {
  if (touch1detected) {
    touch1detected = false;
    if (touchInterruptGetLastStatus(T7)) {
      digitalWrite(48,HIGH);

      tone(46,400,300);
      tone(46,240,250);

    } else {
      digitalWrite(48,LOW);
    }
  }
  
  delay(100);

}
```

{% embed url="https://vimeo.com/1168270596?fe=ci&fl=sv&share=copy" %}

Above is the video of the interactive microcontroller

#### Refelection

With Embeded programing, I understand how the microcontroller work and how to use the datasheet to understand its function more systematically. Before, I began to use it without knowing too deeply, but I was more focusing on the hands-on part. With understanding of how each pin is, I could explain it more clear to someone else if they don't understand.
