---
layout: post
title:  "01-Creative Coding - Random dots "
date:   2022-08-12 16:01:18 +1000
categories: jekyll update
---


# 🌟 Concept 🌟 # 
This page uses ``` Random() ``` to try two different simple effects to show interactive and colorful images.

🌟The first one is a random color, where various colored circles are randomly distributed.

🌟The second one is a combination of randomly sized circles and random colors, trying to make a three-dimensional painting.

<iframe width=600 height=442 src="https://editor.p5js.org/LuciaOvO/full/d97qMJSTB"></iframe>

# 🌟 Code & Comments 🌟 

```javascript
//Set the position variable of the dot
var spot ={ //Set a class of variable name "spot"
  x:50, // set variable "spot.x" equal to 0
  y:100 // set variable "spot.y" equal to 0
};

//Set the color variable of the dot
var col={ //Set a class of the color variable of the dot name "col"
  r:0,  // set variable "col.r" equal to 0
  g:0,  // set variable "col.g" equal to 0
  b:0   // set variable "col.b" equal to 0
};

function setup() {  // runs once, at the start
  createCanvas(600, 400); // creating a canvas
                            // 600 pixels wide &
                            // 400 pixels tall
  
  //The background is run only once to reach the dot can be iterated
  background(220);
}



function draw() {  // loops, after setup has run
// Make dots randomly generated in Canvas 
  spot.x=random(0,width); 
  spot.y=random(0,height);
  
//  random color in RGB range 
  col.r=random(100,255); // The range of red random is 100-255
  col.g=random(0,200); //Green random range is 0-200
  col.b=random(0,255); //The range of blue random is 0-255
  
//---dots set up---
 
  fill(col.r,col.g,col.b); //set dots color fill Red control by "col.r"
                           //green control by "col.g"
                           //blue control by "col.b"
  
  // no outline
  noStroke();

  // The x position of the circle is controlled by spot.x and the y position is controlled by spot.y. The diameter of the circle is 20.
  ellipse(spot.x,spot.y,20);   
}
```


<iframe width=740 height=442 src="https://editor.p5js.org/LuciaOvO/full/QDEnFcaCf"></iframe>
# 🌟 Code & Comments 🌟

```javascript
var col={ //Set a class of the color variable of the dot name "col"
  r:0,  // set variable "col.r" equal to 0
  g:0,  // set variable "col.g" equal to 0
  b:0   // set variable "col.b" equal to 0
};

var size = { // set a class of the size variable of the dots name "size"
  X: 0,  // set variable "size.X" equal to 0
  Y: 0  // set variable "size.Y" equal to 0
}

function setup() { // runs once, at the start
  createCanvas(750, 400); //// creating a canvas
                            // 750 pixels wide &
                            // 400 pixels tall
}

//The background is run only once to reach the dot can be iterated
  background('BLACK'); // set background color to "BLACK"
}

function draw() {  // loops, after setup has run
  // random color in RGB range 
  col.r=random(100,255); // The range of red random is 100-255
  col.g=random(0,200); //Green random range is 0-200
  col.b=random(200,255); //The range of blue random is 200-255
  
  size.X= random(5,20); // size.X has a value range of 5 to 20
  size.Y= random(5,20);  //Size.Y has a value range of 5 to 20
  
//--Dots set up--
  
  // no outline
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


