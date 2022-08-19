---
layout: post
title:  "Creative Coding - Random dots "
date:   2022-08-12 16:01:18 +1000
categories: jekyll update
---


# 🌟 Concept 🌟 # 
This page uses ``` Random() ``` to try two different simple effects to show interactive and colorful images.

🌟The first one is a random color, where various colored circles are randomly distributed.

🌟The second one is a combination of randomly sized circles and random colors, trying to make a three-dimensional painting.

<iframe width=600 height=442 src="https://editor.p5js.org/LuciaOvO/full/d97qMJSTB"></iframe>
# 🌟 Code & Commends 🌟 

```javascript
//Set the position variable of the dot
var spot ={
  x:50,
  y:100
};

//Set the color variable of the dot
var col={
  r:0,
  g:0,
  b:0
};

function setup() {
  createCanvas(600, 400);
//The background is run only once to reach the dot can be iterated
  background(220);
}

function draw() {
// Make dots randomly generated in Canvas 
  spot.x=random(0,width);
  spot.y=random(0,height);
  
//  random color in RGB range 
  col.r=random(100,255); // The range of red random is 100-255
  col.g=random(0,200); //Green random range is 0-200
  col.b=random(0,255); //The range of blue random is 0-255
  
//dots set up
  fill(col.r,col.g,col.b);

  // no stroke 
  noStroke();

  // The x position of the circle is controlled by spot.x and the y position is controlled by spot.y. The diameter of the circle is 20.
  ellipse(spot.x,spot.y,20);   
}
```


<iframe width=740 height=442 src="https://editor.p5js.org/LuciaOvO/full/QDEnFcaCf"></iframe>
# 🌟 Code & Commends 🌟 

```javascript
//Set the color variable of the dot
var col={
  r:0,
  g:0,
  b:0
};

// set up X,Y Related to circle size
var size = {
  X: 0,
  Y: 0
}


function setup() {
  createCanvas(750, 400);
//The background is run only once to reach the dot can be iterated
  background('BLACK');
}

function draw() {
  // random color in RGB range 
  col.r=random(100,255); // The range of red random is 100-255
  col.g=random(0,200); //Green random range is 0-200
  col.b=random(200,255); //The range of blue random is 200-255
  
  size.X= random(5,20); // size.X has a value range of 5 to 20
  size.Y= random(5,20);  //Size.Y has a value range of 5 to 20
  
//--Dots set up--
  
  // no stroke 
  noStroke();
  
  //The RGB color of the ellipse is controlled by col.r,col.g,col.b variables respectively
  fill(col.r,col.g,col.b);
  
  
  // Randomly generate different colors according to the movement of the mouse
  // The x-axis and y-axis coordinates of the ellipse are controlled by the x-axis and y-axis of the mouse, respectively.
  //The size is controlled by the random values of the variables size.X, size.Y.
  ellipse(mouseX, mouseY, size.X, size.Y);
  
  //Set another ellipes, set transparency to 50
  fill(col.r,col.g,col.b,50);

  // mouseX+17: move along the mouse X axis while deviating by 17
  //mouseY+20: move along the mouse Y-axis while deviating by 20
  ellipse(mouseX+17, mouseY+20, size.X, size.Y);
   
}


```


