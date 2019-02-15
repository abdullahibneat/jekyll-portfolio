---
title: "GoldenIsland: The Treasure Map"
description: "A complete adventure map game where Delton, a pirate, wants to find and take a treasure hidden inside the forest."
layout: post

media-folder: "GoldenIsland"
featured: "ft.jpg"
skills: [3D Modelling, Texturing, Unreal Engine]
---
*Models created in **3DS Max**, textured in **Photoshop**. Game produced and packaged in **UnrealEngine 4**.*

<iframe width="100%" height="315" src="https://www.youtube.com/embed/PbeNuS-agbg" frameborder="0" allowfullscreen></iframe>

The creative computing course I'm currently undertaking includes a unit where I'm required to plan and produce a computer game based on client requirements. I decided to use my skills in 3DS Max and UnrealEngine to produce a 3D, first person adventure game.

![{{ post.title }}]({{ site.url  }}/{{ site.media-folder }}/{{ page.media-folder }}/1.jpg)

**GoldeIsland: The Treasure Map** is a third-person adventure game located in a lost island. Delton 'Four-Teeth' Foy, the main character of the game, is a pirate who found a treasure map while going through his father’s old belongings, and determined to find the mysterious treasure.

The client required the game to be suitable for the _age range 8-12_, include _collectable items_, _traps_ or _AI_ that reduce the _limited number of lives_, and the player performance _based on the duration of the gameplay_.

Firstly, I produced a design document so to have clear ideas on what I should include on the game, the story behind it and think of game mechanics I could use as well as an art style. The plan included the creation of two levels (an island and a temple), use of simple game mechanics, a key required to enter the temple level, and parkour over the lava for the second level. For the art style, I decided to go for a mix of low-poly assets and realistic textures.

I produced a block out of the first level inside Unreal Engine, where I used the Landscape Tool to create the main island and BSP brushes to make a very simple temple. I then began modelling the assets inside 3DS Max: this included the creation of a variety of trees, rocks, the temple and a boat. Programming was next with the use of blueprints to trigger events and display user interfaces. I repeated the same process for the second level.

![{{ post.title }}]({{ site.url  }}/{{ site.media-folder }}/{{ page.media-folder }}/2.jpg)

Throughout the development, I continuously tested the game, and this allowed me to find some issues. For instance, I had huge performance issues with the first level given the number of trees put in place. I was able to fix this using L.O.D. (level of detail) which loads the 3D model of the tree within a certain range of the player, while showing a simple plane with the tree as a texture in the distance.

![{{ post.title }}]({{ site.url  }}/{{ site.media-folder }}/{{ page.media-folder }}/3.jpg)

![{{ post.title }}]({{ site.url  }}/{{ site.media-folder }}/{{ page.media-folder }}/4.jpg)

![{{ post.title }}]({{ site.url  }}/{{ site.media-folder }}/{{ page.media-folder }}/5.jpg)

![{{ post.title }}]({{ site.url  }}/{{ site.media-folder }}/{{ page.media-folder }}/6.jpg)

A second problem arose with the scoring system: client requirements mention that the score is based on the play time, so the quicker the player completes the game, the higher the score. Fortunately, I came up with a mathematical solution with the use of the reciprocal function _y = 1/x_, with _y_ being the score and the _x_ representing the time.

Finally, I packaged the game for Windows devices and used cinematic cameras to produce some in-game footage.