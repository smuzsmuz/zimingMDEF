---
icon: '2'
---

# Intervention: Understanding GSR sensor

This intervention is a continuation from the micro challenge, where I teamed up with Carlos and Javi to create a wearable (a GSR sensor triggering ferrofluid to show human emotional state with  a pH indicator suface to determine the sweat situation).  We didn't finish the project because 1. we didn't understand the data from the GSR sensor; 2. We need to complete the silicone container for ferrofluid; 3. We need to optimize the pH layer.

In my part, I am creating this intervention to understand GSR sensor, to see if we should change the designed input for the wearable for change the output of the GSR data.

**GSR sensor's introduction says that the two electrodes measure the conductivity of the skin, higher numbers means higher conductivity which could mean more moist.**&#x20;

````
// ```cpp
const int GSR=A5;
int sensorValue=0;
int gsr_average=0;

void setup(){
  Serial.begin(9600);
}

void loop(){
  long sum=0;
  for(int i=0;i<10;i++)           //Average the 10 measurements to remove the glitch
      {
      sensorValue=analogRead(GSR);
      sum += sensorValue;
      delay(5);
      }
   gsr_average = sum/10;
   Serial.println(gsr_average);
   int human_resistance = ((1024+2*gsr_average)*10000)/(516-gsr_average);
   Serial.print("human_resistance=");
   Serial.println(human_resistance);
   delay(2000);
}

````

* When no one is wearing the sensor the number is 432.
* Different people have different range of number, for example: my range is around 250-350.

<figure><img src="../../../.gitbook/assets/Screenshot 2025-02-12 152127.png" alt=""><figcaption></figcaption></figure>

<details>

<summary>Question?</summary>

Does the sensor tell emotion?

Some people always have sweat in hand, Some people don't.

</details>

{% stepper %}
{% step %}
### Why do our body have conductivity?

Excitable cells, such as neurons (nerve cells) and muscle cells are polarised, that is, the inside of each cell is negative with respect to the outside. This negative potential difference is caused by an unequal distribution of ions on either side of the cell membrane. Movement of these ions across the cell membrane generates an electrical pulse known as an action potential. Our nervous system uses these action potentials to send signals around our body.
{% endstep %}

{% step %}
### How does nervous system construct?

<figure><img src="../../../.gitbook/assets/Screenshot 2025-02-12 155135.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### What does it mean to have more sweat in body?

Chinese medical understanding:

Western scientific understanding:
{% endstep %}

{% step %}
### What does it mean to have a high conductivity in skin?

<figure><img src="../../../.gitbook/assets/Screenshot 2025-02-07 113827.png" alt=""><figcaption></figcaption></figure>


{% endstep %}
{% endstepper %}

## Streamgraph: Processing and GSR data of me

