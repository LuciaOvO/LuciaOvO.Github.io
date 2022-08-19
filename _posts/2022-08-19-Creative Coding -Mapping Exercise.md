---
layout: post
title:  "Creative Coding - Mapping Exercise "
date:   2022-08-13 16:01:18 +1000
categories: jekyll update
---

# 🌟 Concept 🌟 

Interaction Ideas-Use the mouse to move to change the background color or use the automatic movement of the graphics to change the background color to achieve interaction

<iframe width=400 height=442 src="https://editor.p5js.org/LuciaOvO/full/HGAfU61Y6"></iframe>



# 🌟 Code & Commends 🌟 

```javascript
//Set variables for each of the RGB colors Red and Blue 
var r = 0;
var g = 255;

function setup() {
  createCanvas(400, 400);
}
```


**Testing**
: I did the test in the simplest way first. The circle moves with the X-axis of the mouse while the background color changes. 
```javascript
function draw{
   col=mouseX;
   background(col); 
   fill("hotpink");
   ellipse(mouseX,200,64,64);
}
```

**Practical** 
: Then wrote simpler methods based on how ```Map()``` is used, which made my code look less cluttered.

```javascript
function draw() {
  //Use Map () to map the values in the range to new values in the range with the others 
  //Mouse X has a range of 0-400 and maps this range to 0-255,the content assigned to the variable color
  r = map(mouseX,0,400,0,255);
  g = map(mouseX,0,400,255,0); 
 
 //Background set up
  background(r,g,0)
 
 //ellipse set up
  fill("hotpink");
  ellipse(mouseX,200,50,50);
  noStroke();
   
}
```