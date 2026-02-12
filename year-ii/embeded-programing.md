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
