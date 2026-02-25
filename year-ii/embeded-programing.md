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

#### Interact with ESP32 , touch the board and make it blink and sing

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
