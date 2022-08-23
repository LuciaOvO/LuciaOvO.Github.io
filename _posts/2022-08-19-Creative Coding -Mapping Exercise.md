---
layout: post
title:  "02-Creative Coding - Mapping Exercise "
date:   2022-08-13 16:01:18 +1000
categories: jekyll update
---

# 🌟 Concept 🌟 

Interaction Ideas-Use the mouse to move to change the background color or use the automatic movement of the graphics to change the background color to achieve interaction

<iframe width=400 height=442 src="https://editor.p5js.org/LuciaOvO/full/HGAfU61Y6"></iframe>



# 🌟 Code & Comments 🌟 

```javascript
//Set variables for each of the RGB colors Red and Blue 
var r = 0; // The value of red is 0
var g = 255; //The value of green is 255

function setup() { // runs once, at the start
  createCanvas(400, 400);   // creating a canvas
                            // 400 pixels wide &
                            // 400 pixels tall
}
```

**Testing**
: I did the test in the simplest way first. The circle moves with the X-axis of the mouse while the background color changes from black to white.

```javascript
function draw{  // loops, after setup has run
   col=mouseX;  // "col" equal to mouse x position
   background(col); // background color control by mouse X-axis
   fill("hotpink"); // ellipse fill hotpink this color
   ellipse(mouseX,200,64,64); // ellipse X-axis control by mouse x position
}
```

**Practical** 
: Then wrote simpler methods based on how ```Map()``` is used, which made my code look less cluttered.

```javascript
function draw() {  // loops, after setup has run
  
  //Use Map () to map the values in the range to new values in the range with the others 
  r = map(mouseX,0,400,0,255); // Mouse X has a range of 0-400 
                               // maps this range to 0-255 (the content assigned to the variable color)
  
  g = map(mouseX,0,400,255,0); // Mouse X has a range of 0-400 
                               // maps this range to 255-0 (the content assigned to the variable color)
 //Background set up
  background(r,g,0) // fills the canvas in red = "r",green ="g",blue = 0.
  
  //ellipse set up
  fill("hotpink");//fills the ellipse color "hotpink"
 
  ellipse(mouseX,200,50,50); // ellipse X-axis control by mouse X-axis
  
  noStroke(); // no outline
   
}
```