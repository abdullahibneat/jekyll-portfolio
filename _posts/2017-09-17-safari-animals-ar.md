---
title: "Safari Animals AR"
description: "Augmented reality project featuring safari animals, created as part of an internship, to improve my skills in 3DS Max and Unity."
layout: post

imgpath: "SafariAnimalsAR/"
ft: "ft.jpg"
renders: "1.jpg,2.jpg"
---
*Models created, rigged and animated in **3DS Max**, AR app packaged in **Unity**.*

<u>**Try the game now! Head over to the [Google Play Store](https://abdu.io/play) and search *Safari Animals AR*.**</u>

I've been offered an internship opportunity at [Inition](https://www.inition.co.uk/), a leading AR and VR company in London. Throughout my stay, I had the opportunity to work on a personal project aimed to improve my 3D modelling skills with the guidance of the lead 3D artist.

The project consisted in creating an AR app for mobile devices, inspired by an exhibition of [Marokka](https://marokka.com/) where people could have used an app on their smartphones to see the animals in augmented reality.

<iframe width="100%" height="315" src="https://www.youtube.com/embed/YEAd46worxE" frameborder="0" allowfullscreen></iframe>


I used 3DS Max to create the models. I decided to make them of a low poly count as the target device are smartphones which may not able to render high poly models in real-time. This also meant I could have followed the low poly style throughout the project. The main modifiers I used were the Symmetry modifier and the Noise modifier. I also made sure to clear all Smoothing Groups to enhance the low poly effect.

For animation purposes, I had to rig the animals. Therefore I turned a Biped system into a Quadruped, and set the bones to the correct size and position for each animal. I then applied a Skin modifier to the animals so that I could link the Bones to the model. Finally, I set the Weight of each Bone so that each Bone influences a certain part of the model (i.e. foot bone only affects the foot of the animal and not the head).

Lastly, I created a walk cycle for each animal. I found out the Copy/Paste rollout in the Motion panel to be a fast way of creating animations. I therefore used Google to find sketches of walk cycles for each animal I modelled and imported them into my scene as a reference. The next step was to set and copy two poses: the Pass pose and the Contact pose. Using the timeline, and setting Auto Key on, I pasted the poses in order and the 3DS Max did the work of filling out the frames in between the two poses (tweening).

For this project, I decided to have a go with Unity because ① I wanted to explore a variety of software used in the industry, and Unity is one of the most popular one, and ② because Unity has more options in regards of AR plugins. Compared to Unreal Engine, Unity requires coding to make scripts, whereas Unreal Engine includes Blueprint, which I find to be a quicker way for level designing.

During the development of the game level, I decided to use [Vuforia](https://vuforia.com/) as the AR platform. This package enables me to quickly prototype AR apps by just importing two Prefabs (an AR camera and an imageTarget for the AR marker), and set a custom marker. Also, I used the CrossPlatformInput package to enable the player to control the animals' movement.

Overall, I had to code two C# scripts: one is responsible for moving the animal in the joystick's direction while playing the walk cycle animation (otherwise play the idle animation); the second script spawns an animal when its button is pressed on the UI.

Finally, I packaged the Unity scene for Android devices, and run the app on my device to check for correct operation and any unexpected behaviour.
