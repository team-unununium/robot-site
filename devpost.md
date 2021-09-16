---
layout: default
---

# Original Devpost

The following is a copy of our original Devpost, which can be found [here](https://devpost.com/software/hnr2020-vr-robot).

## Inspiration
By looking through the award winners of the past year, we originally wanted to make a robot that is as useless and/or annoying as possible. However, we soon realized that there is more uses to making such robots are we originally thought, so our attention shifted to attempting to use the robot to help survivors in extreme conditions, and soon, the VR Robot Explorer came to be. 

## What it does
Basically a robot which is controlled by VR. The robot has two cameras and some sensors which are used to give users data about the environment the robot is in. Input from the camera and sensors is displayed on the VR headset. The clients can rotate their headset, which will cause the robot's camera to rotate in the same direction, and by touching the side button of the headset, the robot will start or stop moving.

## How we built it
The robot was made up of a Rover 5 Chasis with an Arduino microcontroller embedded in it. The Arduino is connected to a Raspberry Pi which sends the results of any abnormal readings along with its camera footage to a server, which sends it all the clients. We used socket.io to facilitate communication between the server and the robot as well as between the server and the clients, and RTMP was used to transmit the video footage to the clients. The Android app also uses Google's Cardboard SDK. 

## Challenges we ran into
Some of the hardware was prone to failure and we ended up wasting quite a lot of time attemping to repair them. In addition, 

## Accomplishments that we're proud of
Despite the limited time constraints, we managed to finish nearly all of the project in the time that we were given, only delayed by some technical difficulties that we weren't expecting. Besides, we also work until the last second even though we may not be able to complete the project at all.

## What we learned
We had learnt how to be resourceful and utilize the tools that we have around us to overcome the challenges that we face. We had also learnt to be patient and careful when doing our work to reduce the chance of mistakes.

## What's next for VR Robot Explorer
After the hackathon, we plan to fully complete the VR Robot Explorer and test it in perilous conditions to test its potential. We also plan to participate in future hackathons. 
