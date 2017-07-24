---
title: "Getting to Know Unreal Engine"
description: "A Google Cardboard VR project I made in Unreal Engine 4 to getting used to the basics of this game engine."
layout: post

imgpath: "UnrealBasics/"
ft: "ft.jpg"
renders: "1.jpg,2.jpg,3.jpg"
---
*Assets created in **3DS Max**, VR scene composed in **Unreal Engine 4** and video edited and rendered in **Premiere Pro**.*

As part of my course requires me to produce a game, I thought I'd explore the basic tools of Unreal Engine 4 prior to my learning in class. I decided to make a Google Cardboard VR project as my school has VR equipment, thus learning how to create a virtual reality environment from scratch. During the development, I learned how to use a variety of Unreal Engine's built-in tools, such as the Landscape Editor, the Foliage Tool, the Material Editor, Cinematics and the Blueprint Visual Scripting.

I started by creating a blank project with "Mobile / Tablet" as target hardware, "Scalable 3D or 2D" graphics and no starter contents. Then I set up the project to be compatible with Google Cardboard (i.e. enable the Google VR plugin and set the API Levels). Before proceeding any further, I packaged an empty project with one floor to test it in VR.

The first step was to create the landscape. I therefore created a Landscape Material with the Layer Blend node connected to the Base Colour. This node included two Constant3Vectors: a green one for the grass and a brown one for the dirt. I also applied some other nodes to the Normal of the material for the low poly effect. Finally, I created a landscape using the brush from the Landscape Editor. This included the creation of a hole for the lake.

Secondly, I imported some trees and rocks I previously modelled in 3DS Max. I then placed these assets in the Foliage Tool so I could have easily populated the scene with vegetation. I tried to not over-populate the scene as this would have an impact on the performance of the end device.

Later I created a water material for the lake. I did this by downloading a normal map for water and by using an online tool I made it look low poly. I then created the material by using the Lerp node as the Base Colour to blend two tonalities of blue, and I used the Panner with the normal map to animate the water. I also placed a TexCoord note to the Panner to regulate the size of the texture. I then placed a BSP box big enough to cover the lake and applied the water texture. As I prdicted, I had to change the value of the TexCoord to make the size of the normal map smaller.

Afterwards I had to provide the user with a navigation system. I therefore created a Blueprint Class for the user, added a teleportation system which makes use of Traces, and I placed a cylynder to mark the teleport location. I then added an input event which triggers the teleportation to happen. Finally, I set up a new Trace Channel so to limit the user teleportation within an area marked with Blocking Volumes.

The last step was to add sounds. I found some forest sounds, a campfire sound and a lake sound. I imported them into the engine, created a Sound Cue and added a Loop node for each of these. I then placed the Sound Cues in the scene and set the Attenuation Sphere radius so that the sound could be heared when the user is close to the given object.

Finally, I packaged the project for my Android device and tested it out!

<iframe width="100%" height="315" src="https://www.youtube.com/embed/YvxGUpy1YLg" frameborder="0" allowfullscreen></iframe>
