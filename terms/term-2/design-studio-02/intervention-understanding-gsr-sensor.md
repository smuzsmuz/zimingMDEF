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
### What does it mean to have constantly high conductivity in skin?

<figure><img src="../../../.gitbook/assets/Screenshot 2025-02-07 113827.png" alt=""><figcaption></figcaption></figure>

#### Chinese medical understanding: Heart and mental activity, liver and Qi  (气) flow

* **Persistent high conductivity**: May indicate **“yin deficiency with yang hyperactivity”** or **“internal phlegm-heat,”** requiring yin-nourishing and heat-clearing therapies.
* **Low conductivity with instability**: Suggests **“heart-spleen deficiency”** or **“weak defensive qi,”** addressed by tonifying qi and consolidating the exterior.

#### **Western Physiological Perspective**

A **high GSR value** (increased skin conductivity) reflects:

1. **Sympathetic Nervous System Activation**: Stress, anxiety, fear, or excitement trigger the "fight-or-flight" response, causing sweat glands to secrete more electrolyte-rich fluid. This increases skin conductivity.
2. **Emotional Arousal**: Strong emotions (positive or negative) elevate GSR readings.
3. **Environmental Stimuli**: External factors like heat, pain, or sudden sensory input can also raise GSR.
{% endstep %}

{% step %}
### What does it mean to have a constantly low conductivity in skin?

#### **Western Physiological Perspective**

A **low GSR value** (decreased skin conductivity) suggests:

1. **Parasympathetic Dominance**: The body is in a "rest-and-digest" state, such as during deep relaxation, meditation, or sleep.
2. **Reduced Sympathetic Activity**: Minimal emotional arousal (e.g., boredom, calmness) or suppressed stress responses.
3. **Physical Factors**:
   * **Dehydration**: Reduced sweat production lowers skin conductivity.
   * **Hypothermia**: Cold temperatures constrict blood vessels and decrease sweat gland activity.
   * **Chronic Fatigue or Illness**: Conditions like adrenal fatigue or autonomic nervous system dysfunction may dampen physiological reactivity.

#### Chinese medicine perspective

**1. Qi and Blood Deficiency (气血两虚)**

* **Heart-Spleen Deficiency (心脾两虚)**: Weakness in the Heart (governing blood circulation) and Spleen (governing qi production) leads to poor nourishment of the skin and muscles, resulting in reduced sweat secretion and low conductivity.
* **Symptoms**: Fatigue, pale complexion, poor concentration, and cold limbs.

**2. Yang Deficiency (阳虚)**

* Insufficient Yang energy (warming, activating force) fails to mobilize fluids and qi, causing:
  * **Cold stagnation**: Poor circulation and reduced sweating (low GSR).
  * **Spleen-Kidney Yang Weakness**: Chronic fatigue, edema, and intolerance to cold.

**3. Wei Qi (Defensive Qi) Weakness (卫气不固)**

* Weak Wei Qi fails to regulate skin pores, leading to either excessive sweating (paradoxically low GSR if dehydrated) or inability to sweat appropriately.

**4. Emotional Suppression or Stagnation (气郁)**

* Chronic emotional repression (e.g., unresolved grief, chronic depression) may stagnate Liver qi, dampening physiological reactivity and reducing GSR fluctuations
{% endstep %}

{% step %}
### My status

{% embed url="https://drive.google.com/file/d/1L5rzDykm0Jim-yBbps7cvhERX6MZRJse/view?usp=sharing" %}

When do I have high value of conductivity?

Stressed, illness, pain in body, cold

but also when I feel active and excited.

I want to try meditation.
{% endstep %}
{% endstepper %}

