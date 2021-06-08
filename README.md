# Project-plan
This repository will hold the plan for my upcoming project.

I don't currently have a lock on my door, and with the open floorplan of my house, I find it hard to get any privacy a lot of the time.
In this project, I hope to create a automated door lock that will be able to be controlled at a distance, by a bluetooth remote or something of that sort. 

Link to drawing I made: https://docs.google.com/document/d/15hXM1ehzYP2BAr46WJeZYWaUQpSTp2rlDqFpcUuxJro/edit?usp=sharing

Schedule:
2/7  Finish an inital design for the main panel of lock, with the ability to screw in all needed parts to begin testing.
2/14 Finish designing the piece that goes on the door, which will recieve the steel rod to lock the door.
2/21 Begin writing and testing code, starting with the code to control the locking mechanism.
2/28 Begin writing and testing code to connect the lcd with the locking mechanism.
3/7  Finish first prototype
3/14 Revise lock panel design in CAD
3/21 Revise code
3/28 Put new revisions together and test them
4/4  Finish



# Link to Screenshots of project so far:
https://docs.google.com/document/d/1cxwLfFTIROh1lr6mtTC1lKPVn6btYVll7Q6gUH0OroA/edit?usp=sharing




# Start to Code:
Since I knew I wouldn't have enough time or knowlege of coding to make the project lock off of a bluetooth button press, I decided to change it so It would lock at the press of a button. I didn't have a chance to test the code, so I'm not sure if it is %100 correct.
Link to screenshot of wiring: https://docs.google.com/document/d/1UQkuc7b1siGJEz3E8N7Q3u_pw4t0nJb3b0EvhvoUcLc/edit?usp=sharing 

#include<Servo.h>
int pos = 90;
int pin4 = 4;
int pin3 = 3;
int LedHi = 5;
int LedLow = 6;
Servo servo1;

void setup() {
  pinMode(LedHi, OUTPUT);
  pinMode(LedLow, OUTPUT);
  pinMode(pin4, INPUT);
  pinMode(pin3, INPUT);
  Serial.begin(9600);
  servo1.attach(9);
}

void loop() {
  while (digitalRead(pin3) == HIGH && pos < 180) {
    digitalWrite(LedLow, LOW);
    pos++;
    servo1.write(pos);
    Serial.print("Degrees rotation= ");
    Serial.println(pos);
    if (pos == 180) {
      Serial.print("Reached top end ");
      digitalWrite(LedHi, HIGH);
    }
    delay(10);
  }

  while (digitalRead(pin4) == HIGH && pos > 0) {
    digitalWrite(LedHi, LOW);
    pos--;
    servo1.write(pos);
    Serial.print("Degrees rotation= ");
    Serial.println(pos);
    if (pos == 0) {
      Serial.print("Reached low end ");
      digitalWrite(LedLow, HIGH);
    }
    delay(10);
  }
}


# What I learned while working on this project:
With such little in-class time this year, getting this project anywhere close to done was very hard. I have always had a lot of questions about the different engineering software, especially coding. Many times on zoom, I felt like I couldn't get the answers to these questions as easily as when I have been in class in the past. This isn't anyones fault, it was just a consequence of the odd circumstances we faced this year. Onshape was really cool to use and learn, and I liked it's ability to work on projects from home. I don't have a mouse at home which made it hard to effectively work on parts at home, but this didn't play too much of a factor. I realized that when I fell off of my schedule I began to fall behind, which led to me being unable to finish my project. Procrastination and distractions got the better of me, and I need to figure out different ways to keep me on track during a project. It would have been nice to finish my project, but I am happy with what I have learned this year, as limited as it may be. Thanks for a great year!
