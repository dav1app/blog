---
layout: post
title:  "I speed-learned Flutter"
image: /assets/images/flutter-logo.png
---

My favorite thing about Hollywood hackers is how fast those nerds learn new platforms. I mean, The Hackerman enters the most advanced datacenter in the universe, and suddenly knows how to access every server in the room.

Well, I've tested speed-learning a new platform - Dart - by creating a single screen on it. It took me 10h35 to install Flutter, force-learn the basics and start developing. There is no logic happening on the screen.

![App]({{ BASE_PATH }}/assets/images/flutter-app.png)

Important notes: I hate Java and I hate Android Studio.

## Dart is not Googles Javascript
It feels more like Java than Javascript. I know when those guys intersect, but JSs main goal is to be flexible and Dart seems to like the philosophy that "everything is a class". 

## Is hard to style elements in Flutter
Since everything is a class, you need to specify proprieties to the classes, and these proprieties are other classes, and you need to specify the proprieties to it. This goes on and on, and I still don't know why frameworks don't accept the CSS-way for styling elements.

## There is no good input component in Flutter, and I don't know the reason why
In Java you have some similar problems. I hate that. It forces you to find some components outside the framework. Since Flutter creates a good pack of buttons, why not implementing an input component?

## Material design is bad for drafting ideas
Since I was speedruning, most of the components I've started drafting was in the components given by Flutter. This became a problem really quickly when I need something that is "wrong" in the material design world. There is 9 types of buttons in Flutter, none of them was simple enought to make that little green button. 

## Flutter has a different way to think about rows and cols.
This was a hard for someone that uses Bootstrap a lot. When you specify something as a Row, the elements inside it are displayed horizontally even if the element isn't a column. It took me a while to figure it out. 


