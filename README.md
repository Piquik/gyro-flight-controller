# gyro-flight-controller
my very first repository ! in here i want to start by learning basic electronics, then eventually make a very cool gyro powered flight controller.

## Step 1, actually learning electronics
right now, I'm focusing a lot on the **foundations of electronics**, for that I'm following an online Youtube course by @CodeNMore, here's the link: https://www.youtube.com/watch?v=r-X9coYTOV4&list=PLah6faXAgguOeMUIxS22ZU4w5nDvCl5gs

Here are a couple of notes i took:

<img width="400" alt="Notes" src="https://github.com/user-attachments/assets/685f012e-f994-4db8-9175-47dc557cc9b0" />

### log 1, let there be LEDs

That's pretty neat, I've made light
<img width="200" alt="IMG_2066" src="https://github.com/user-attachments/assets/4b5bb394-760d-4bf7-96bb-5429fb9cf6e0" />
<img width="200" alt="IMG_2065" src="https://github.com/user-attachments/assets/abcdf9c5-c914-4daa-9aa8-d805bbd5fc76" />

the actual circuit is stupidly simple, one 9v battery, an MB102 power module and a blue LED.
I learned that polarity sorta matters a lot, and i know how a breadboard works, **hooray** !

### log 2, wooo hoooo motion !

Yay ! I made a motion sensor ! I mean I didn't make it, that was probably done from some assembly line in China, but i made it work ! i used an HC-SR501 module, basically just 
a fancy word for an infrared motion detector, which i plugged into an arduino Uno, call me Ironman.

<img width="400" alt="IMG_2069" src="https://github.com/user-attachments/assets/f8b14829-c550-4c29-9676-5c60be109f29" />


<div align="center">
  <video src="https://github.com/user-attachments/assets/3a68543b-0e35-4be4-9b8a-3132fed5f794" width="200" controls></video>
</div>


Turns out even Ironman has to comply to the github 10 MB limit


Here's the code I used in the IDE:

```plaintext
const int pirPin = 2;
const int ledPin = 13;

void setup() {
  pinMode(pirPin, INPUT);
  pinMode(ledPin, OUTPUT);

  Serial.begin(9600);
  Serial.println("Waiting 30s for sensor to calibrate...");

  delay(30000);

  Serial.println("Ready");
}

void loop() {
  if (digitalRead(pirPin) == HIGH) {
    digitalWrite(ledPin, HIGH);
    Serial.println("motion detected");
  } else {
    digitalWrite(ledPin, LOW);
  }


  delay(100);
}
```
