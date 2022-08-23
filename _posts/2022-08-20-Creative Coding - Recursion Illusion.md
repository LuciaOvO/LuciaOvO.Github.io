---
layout: post
title:  "03-Creative Coding - Recursion illusion"
date:   2022-08-16 16:01:18 +1000
categories: jekyll update
---



# 🌟 Concept 🌟 
It was a process of concept development, first learning the first iteration of a simply made graphic based on a tutorial on Youtube, then changing it as well as being inspired to make a space tunnel-like feel, adding his own ideas and his own code to the tutorial to make him look dreamy and spacey.

<iframe width=576 height=366 src="https://editor.p5js.org/LuciaOvO/full/7QBJzSbEa"></iframe>



# 🌟 Code & Comments 🌟 

**sketch.js**
```javascript
let Rectangles = []; // Object Array setting
                     // declare variable "Rectangles"
                     // assigning to it an empty array

let increment = 0; // set a variable "increment" Equal to 0

function setup() { // runs once, at the start
  createCanvas(576, 324);  // creating a canvas
                          // 576 pixels wide &
                         // 324 pixels tall 
 
  //Make the rectangle completely in the middle of the screen
  // By use CENTER mode
  rectMode(CENTER); 
  
  //Change the mode to DEGREES
  angleMode(DEGREES);
}

function draw() { // loops, after setup has run
  
  increment++; // "increment" is always increasing
  
   background("BLACK"); // fill canvas background color "black"
  
  //Increment value, generates after 10 frames. 
  if(increment > 10){ // if increment greater than 20 
     
    // then push this "Rectangle" object into this "Rectangles" array
    Rectangles.push(new Rectangle()); 
    
    increment = 0; // let increment equal to 0
  }
  
  // Loop according to the length of the Array
  for(let i = 0; i < Rectangles.length; i++){ // set up a variable "i"
                                              // let "i" equal to 0
                                              // "i" less than rectangles dot length,loop through the entire array
                                              // "i" equal to "i" plus 1
    
    Rectangles[i].update(); // Run Rectangles[i].update this function
    
    Rectangles[i].show();// Run Rectangles[i].show this function
    
    //Remastered Array，disappear images that exceed a certain number of pixels
    if(Rectangles[i].gone()){ // if Rectangles[i].gone() this function run
    Rectangles.splice(i,1); // then deleteCount 1
    }
  }    
}
```

**rect.js**

```javascript
//Create a class so that can have multiple rectangles at the same time
class Rectangle { // create a class name "Rectangle"
  constructor(){ // create a function in the class name "constructor"
    
    
    this.size = 5; //this rectangle size initially set to 5 
    
    this.rotation = 0; // this rectangle rotation initially set to 0

    
  }
  
  update(){ // create a function in the class name "update"
    this.size++; //Set size to larger update
                 //this.size equal to this.size plus 1
    
 
    
    this.rotation++; //Set rotation to update
                     //this.rotation equal to this.rotation plus 1

  }
  
  show(){ // create a function in the class name "show"
    
    push(); // Start a new drawing state
    
    translate(width/2,height/2); // Translate to one-half the width
                                // Translate to one-half the height
    
    rotate(this.rotation);//angleMode is "this.rotation"
  
    
    noFill(); // No color filling
    stroke("white")
    rect(0,0,this.size,this.size);// Draw a rectangle at location (0, 0) with a width and height of "this.size"
    
    pop(); // Restore original state
        
  }
  
    //Set a function to make the shape return
    gone(){
       //More than 300 then return
       return this.size > 300
    } 
}
```

<iframe  width=576 height=366 src="https://editor.p5js.org/LuciaOvO/full/jXMqUjjcf"></iframe>

# 🌟 Code & Comments 🌟 

**sketch.js**

```javascript
let Rectangles = []; // Object Array setting
                     // declare variable "Rectangles"
                     // assigning to it an empty array


let increment = 0; // set a variable "increment" Equal to 0

//Object Array setting
// declare variable "Rectangles"
// assigning to it different color array
const rectcolor =[ 
    "#F94892",
    "#FF7F3F",
    "#FBDF07",
    "#89CFFD",
    "#2155CD",
    "#0AA1DD",
    "#79DAE8",
    "#E8F9FD"
  ];

function setup() { // runs once, at the start
  createCanvas(576, 324);  // creating a canvas
                          // 576 pixels wide &
                         // 324 pixels tall 
  frameRate(30); //
  
  //Make the rectangle completely in the middle of the screen
  rectMode(CENTER); // By use CENTER mode
  
  angleMode(DEGREES);//Change the mode to DEGREES
  
}


function draw() { // loops, after setup has run
  
  background(0,20); // fill canvas background color "grey"
  
  //----rect object----
  increment++; // "increment" is always increasing
  
  //Increment value, generates after 10 frames. 
  if(increment > 40){ // if increment greater than 20 
     
    // then push this "Rectangle" object into this "Rectangles" array
    Rectangles.push(new Rectangle()); 
    
    increment = 0; // let increment equal to 0
  }
  
    
  
  // Loop according to the length of the Array
  for(let i = 0; i < Rectangles.length; i++){ // set up a variable "i"
                                              // let "i" equal to 0
                                              // "i" less than rectangles dot length,loop through the entire array
                                              // "i" equal to "i" plus 1
    
    Rectangles[i].update(); // Run Rectangles[i].update this function
    
    Rectangles[i].show();// Run Rectangles[i].show this function
    
    //Remastered Array，disappear images that exceed a certain number of pixels
    if(Rectangles[i].gone()){ // if Rectangles[i].gone() this function run
    Rectangles.splice(i,1); // then deleteCount 1
    }
  }  
  //----end rect object----
  
  //---end add star---
  let a=random(0,width) // create a variable "a" 
                        // equal to random interval"(0, width)"
  let b=random(0,height) // create a variable "b" 
                        // equal to random interval"(0, height)"
  
  noStroke(); // no outline
  
  circle (a,b,1) // draw a circle 
                // The x coordinate is controlled by "a"
               // The y coordinate is controlled by b
              // diameter is "1"
  
  circle (a,b,3)// draw a circle 
                // The x coordinate is controlled by a
               // The y coordinate is controlled by b
              // diameter is "3"
  //---end add star---
}
```
**rect.js**

```javascript

//Create a class so that can have multiple rectangles at the same time
class Rectangle { // create a class name "Rectangle"
  constructor(){ // create a function in the class name "constructor"
    
    
    this.size = 5; //this rectangle size initially set to 5 
    
    this.rotation = 0; // this rectangle rotation initially set to 0 
  }
  
  update(){ // create a function in the class name "update"
    this.size++; //Set size to larger update
                 //this.size equal to this.size plus 1
    
    this.rotation++; //Set rotation to update
                     //this.rotation equal to this.rotation plus 1
  }
  
    show(){ // create a function in the class name "show"
    
    push(); // Start a new drawing state
    
    translate(width/2,height/2); // Translate to one-half the width
                                // Translate to one-half the height
    
    rotate(this.rotation);//angleMode is "this.rotation"
    
    //--color change---
    
    noFill(); // No color filling
    let i = floor (frameCount / 100); // create a variable "i"
                                      // Take integer values, ie. with floor
                                      // and through time, ie. with frameCount divide by 100
   
    i = i % rectcolor.length; // "i" equal to "i" multiple of "rectcolor.length" array length
    
    stroke (rectcolor[i]); // outline color on "rectcolor[i]" area
    rect(0,0,this.size,this.size);// Draw a rectangle at location (0, 0) with a width and height of "this.size"
    
    stroke('white'); // the color is "white"
    strokeWeight(10); // Make the points 10 pixels in size
    point(0, this.size);// create a point 
                        //the x-coordinate control by "this.size"
                        //the y-coordinate is 0
    
    stroke(rectcolor[i]); // the color is control by "rectcolor[i]"
    strokeWeight(10); // Make the points 10 pixels in size
    point(this.size,0); // create a point 
                        //the x-coordinate control by "this.size"
                        //the y-coordinate is 0
    
    pop(); // Restore original state      
  }
  
    //Set a function to make the shape return
    gone(){
       //More than 500 then return
       return this.size > 500
    }  
}
```





# 🌟 Reference Link 🌟
<https://www.youtube.com/watch?v=YxOc8AvwQtM>
