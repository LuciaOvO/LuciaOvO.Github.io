---
layout: post
title:  "Assignments 1 p5 Sketch-Space time tunnel"
date:   2022-08-22 16:01:18 +1000
categories: jekyll update
---
# 🌟 Concept 🌟 
Some inspiration and concepts were successfully developed based on some exercises in my blog. I created a clock with a clock as the base element, displayed against the background of the universe, because in the universe time is abstract, I used ```arc()``` to create the seconds, minutes and hours of the clock respectively.

I used ```Random()``` to make a background similar to the starry sky.

Based on the cosmic clock tunneld, I made a line that follows the rotation of the second hand, where the color of the seconds is changeable, and the color of the minutes and hours are fixed, while the whole time is running and rotating itself, just like the Earth has rotation and revolution. This is my concept and the reason why I made this.

<iframe width=576 height=366 src="https://editor.p5js.org/LuciaOvO/full/7E_ZK3lay"></iframe>


# 🌟 Code & Comments 🌟 

**sketch.js**
```javascript

let Circle = []; // Object Array setting
                // declare variable "Circle"
               // assigning to it an empty array


let increment = 0; // set a variable "increment" Equal to 0

//Object Array setting
// declare variable " Circle"
// assigning to it different color array
const rectcolor =[ 
    "#F94892",
    "#C8B6E2",
    "#A8A4CE",
    "#89CFFD",
    "#2155CD",
    "#0AA1DD",
    "#79DAE8",
    "#82DBD8"
  ];

// set up 2 variables called "ARISTOTLE_B" and ",ARISTOTLE_R"
let ARISTOTLE_B,ARISTOTLE_R;

  function preload(){ // set up a preload function 
    
  // load a font file from Fonts folder 
  ARISTOTLE_B = loadFont('Fonts/ARISTOTLE Bold.ttf'); 
    
  // load a font file from Fonts folder
  ARISTOTLE_R = loadFont('Fonts/ARISTOTLE Regular.ttf');
 
  // load a sound effect file from Sound folder 
  song = loadSound('Sound/Space.wav'); 
}

let song; // set up a variable called "song"

function setup() { // runs once, at the start
 createCanvas(576, 324);  // creating a canvas 
                          // 576 pixels wide &
                         // 324 pixels tall 
  
  song.loop(); // Let the background music loop
   
  frameRate(30); //Set frame rate to 30
 

  
  //Make the rectangle completely in the middle of the screen
  rectMode(CENTER); // By use CENTER mode
  
  angleMode(DEGREES);//Change the mode to DEGREES
  
}


function draw() { // loops, after setup has run
  
  background(0,20); // fill canvas background color "black"，opacity of the background is 20.
  
  //----clock object----
  increment++; // "increment" is always increasing
  
  //Increment value, generates after 10 frames. 
  if(increment > 40){ // if increment greater than 20 
     
    
    Circle.push(new Clock()); // run this function 
    
    increment = 0; // let increment equal to 0
  }
  
  // Loop according to the length of the Array
  for(let i = 0; i < Circle.length; i++){ // set up a variable "i"
                                              // let "i" equal to 0
                                              // "i" less than " Circle" length,loop through the entire array
                                              // "i" equal to "i" plus 1
    
    Circle[i].update(); // Run Circle[i].update this function
    
    Circle[i].show();// Run Circle[i].show this function
    
    //Remastered Array，disappear images that exceed a certain number of pixels
    if(Circle[i].gone()){ // if  Circle[i].gone() this function run
    Circle.splice(i,1); // then deleteCount 1
    }
  }  
  //----end clock object----
  
  //----add star BG----
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
  //----end add star BG----
}

function mousePressed(){ // set up a function when mouse pressed it will run 
  
  //If the mouse is clicked while the music is playing, the music is paused
  //Instead, play again
  if(song.isPlaying()){ 
    song.pause();      
  }else{ 
    song.play();
  }
}
```
**Clock.js**

```javascript
//Create a class so that can have multiple rectangles at the same time
class Clock { // create a class name "Clock"
  constructor(){ // create a function in the class name "constructor"
    
    this.size =5; //this rectangle size initially set to 5 
    
    this.rotation = 0; // this rectangle rotation initially set to 0
     
  }
  
  update(){ // create a function in the class name "update"
    this.size++; //Set size to larger update
                 //this.size equal to this.size plus 1
    
    this.rotation++; //Set rotation to update
                     //this.rotation equal to this.rotation plus 1

  }
  
  show(){ // create a function in the class name "show"
    
    let hr=hour(); // create a varibale "hr" equal to "hour()"
    let mn=minute(); // create a varibale "mn" equal to "minute()"
    let sc=second(); // create a varibale "sc" equal to "second()"
    
    push(); // Start a new drawing state
    
    translate(width/2,height/2); // Translate to one-half the width
                                // Translate to one-half the height   
    
    noFill(); // No color filling
   
//---seconds setting------
    
    // create a variable "i"
   // Take integer values, ie. with floor
  // and through time, ie. with frameCount divide by 100
    let i = floor (frameCount / 100); 
    
    // "i" equal to "i" multiple of "rectcolor.length" array length
    i = i % rectcolor.length; 
    
    // outline color on "rectcolor[i]" area
    stroke (rectcolor[i]); 
   
    //create a varibale "secondAngle"
    //map the number of seconds 0-60 to 0-360
    let secondAngle = map(sc,0,60,0,360); 
    
    //create a arc x,y coordinate is 0,0
    //width and height are control by "this.size"
    //and angle mode is "secondAngle" 
    arc(0,0,this.size,this.size,0,secondAngle);

    
//setting minutes and hours angleMode is "this.rotation" 
    rotate(this.rotation);   
    
//----point setting-----    
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
    
//----end point setting---- 

//----minutes setting----
    
    // fill stroke color as rgb(0,180,216)
    stroke(0,180,216);
    
    //stroke weight is 2 pixel
    strokeWeight(2)
    
    //create a varibale "minuteAngle"
    //map the number of minutes 0-60 to 0-360
    let minuteAngle = map(mn,0,60,0,360);
    
    //create a arc x,y coordinate is 0,0
    //width and height are control by "this.size+20"
    //and angle mode is "minuteAngle" 
    arc(0,0,this.size+20,this.size+20,0,minuteAngle);

//----end minutes setting----
    
//----hours setting----
    
    // fill stroke color as rgb(202,240,248)
    stroke(202,240,248);
    
    //create a varibale "hourAngle"
    //map the number of minutes 0-24 to 0-360
    let hourAngle = map(hr,0,24,0,360);
    
    //create a arc x,y coordinate is 0,0
    //width and height are control by "this.size+30"
    //and angle mode is "hourAngle" 
    arc(0,0,this.size+30,this.size+30,0,hourAngle);

    pop(); // Restore original state

//----end hours setting----
//----line setting----
   
   push(); // Start a new drawing state
    
   translate(width/2,height/2); // Translate to one-half the width
                                // Translate to one-half the heigh
    
    strokeWeight(3); // stroke weight is 3 pixel
    rotate(secondAngle); // Angle mode control by "secondAngle"
    stroke(255); // fill line in white color
    line(0,0,150,0); //first point x and y coordinate is 0,0 
                  //secomd poiny x coordinate is 150, y is 0
 
    pop(); // Restore original state

//----end line setting----  
    
//----time text setting----
  push();// Start a new drawing state
  
  translate(width/2,height/2); // Translate to one-half the width
                                // Translate to one-half the heigh
  rotate(secondAngle);// Angle mode control by "secondAngle"
  
  fill("white"); // fill color white
  textSize (10); // font size is 8
  textFont (ARISTOTLE_R); // use ARISTOTLE regular font style
  text("Creative Coding",8,15) // displayed text "RMIT",(x,y) equal to (1,12)
  text("Specialisation",16,30) // displayed text "RMIT",(x,y) equal to (1,12)
    
    
  // fill(rectcolor[i]);// fill color on "rectcolor[i]" area
  stroke(rectcolor[i]); // fill "rectolor[i]" color in font stroke 
  strokeWeight(4); // font stroke weight is 4
  noFill();// no fill color
  textSize (30);// font size is 30 
  textFont (ARISTOTLE_B); // use ARISTOTLE bold font style
  text(" RMIT ",8,-10); // displayed text "RMIT",(x,y) equal to (20,-10)
              
  pop();// Restore original state
    
  push(); // Start a new drawing state
  strokeWeight(1); // stroke weight is 1
  stroke(153); // stroke color is grey
  textSize (10); // font size is 10 
  textFont (ARISTOTLE_R); // use ARISTOTLE regular font style
  translate(10,314); // Translate (x,y) to (10,314)
  text(hr +":"+ mn +":"+ sc, 0, 0); // displayed text "hour"+"minute"+"second",(x,y) equal to (0,0)

  pop(); // Restore original state
  }
  
  //Set a function to make the shape return
    gone(){
       //More than 500 then return
       return this.size > 500;
    }  
}
```