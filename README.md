# HW_1
// Jonathan Turner ID: 42

Section 1:

elevator pic https://imgur.com/a/Lq7D6Tr

elevator gif https://imgur.com/a/cqfn6D1

what is bad with this design is first of all that there are several button looking opject cluttering the real buttons that are used. Also the buttons are not concistant with their placement with the bottom two beining one over the two then every other pair is side by side.
Section 2:

sketch pic https://imgur.com/a/QhZ2KNV

elevators are almost only used to travel between floors so the buttons that are almost are the buttens that select floors. The other ones that are less commonly used are the ones used to open and close the door incase people need to get inside or leave and the doors will not stay open or closed. The last least most common buttons used are to call the firemen or stop the elevator incase of getting stuck or a fire. 
 
in the normlal sequance on events someone would push the call button on the outside then the elevator comes and the user select the floor where the elevator then travles to that floor and drops the user off. 

during this to provide feedback the outside of the elevator there is a screen to show what floor it is at and what way it was travaling. on the inside if you press abutton then it lights up and there is normaly a screen that shows what floor is at.

however with the design that is in the elevator as it is it is possable to accedently sealect the wrong floor it is also possable to not understand what button to press in an emergancy or press one of the emergency buttons insted of selecting at floor. 

to fix this I would put all the floor select buttons over each other and on the left side of the control panel. this provides a design that follows the the design of the floors so the user instenctivly knows how to select the floor. then on the right of those buttons i would put the emergency call and stop buttons under a plastic panel to prevent accadentale pushing. 

Section 3:

project pic https://imgur.com/a/FqozBBd

project gif https://share.getcloudapp.com/Wnuwj501



PImage img,op,close, elevator;
int Timer = 0, elevatorFloor = 358;//start on the first floor 
boolean ePress = false, Emergency = false; 

void setup() {
  size(800, 500);
  img = loadImage("sectionDraft2.jpg");
   op =loadImage("op.png");
   close = loadImage("close.png");
  elevator = loadImage("elevator.jpg");//the celter is 87 px from the edge to then lineing up the x coord it is 250 - 87 = 163 the y for the floors are 563 -> 264
}

void draw() {
   
  background(0);
  // Draw the image to the screen at coordinate (0,0)
  image(img,0,0);
  
  
  fill(216,21,35);
  rect(450, 50, 300, 200);
  
  
  fill(255,255,255);
  //op close buttons
  ellipse(500,400,75,75);
  ellipse(700,400,75,75);
  
  tint(255,127);
  imageMode(CENTER);
 
   image(op,500,400);  
   image(close,700,400);
  imageMode(CORNER);
 
  tint(255,200);
  //elevator setup
  image(elevator,163,elevatorFloor);
  tint(255,255);
  
  
  textSize(32);
  fill(6,26,5);
  textAlign(CENTER);
  text("EMERGENCY ONLY", 600, 150); 
  if (Emergency){
     rect(0, 0, 800, 500);
     textSize(50);
     fill(216,21,35);
     textAlign(CENTER);
     text("EMERGENCY PLEASE WAIT ",400,250);
     text("FOR HELP",400,300); 
     
  }
  else{
      mouseCheck(mouseX, mouseY);
  }
  
  if(ePress){
    
    Timer= Timer+1;
  }
  
}

void mousePressed() {
  if(mouseX >450 && mouseX < 750 && mouseY >50 && mouseY < 250 && ePress == false){
    ePress = true;
  }
  if(mouseX >450 && mouseX < 750 && mouseY >50 && mouseY < 250 && ePress == true && Timer > 5){
   Emergency = true;
   
  }
  
      
      if(mouseX >5 && mouseX < 410 && mouseY >50 && mouseY < 150 && Emergency == false){
    elevatorFloor = 50;
  }  //4th
      if(mouseX >5 && mouseX < 410 && mouseY >150 && mouseY < 256&& Emergency == false){
    elevatorFloor = 154;
  } //3th
      if(mouseX >5 && mouseX < 410 && mouseY >256 && mouseY < 353&& Emergency == false){
    elevatorFloor = 260;
  }  //2th
      if(mouseX >5 && mouseX < 410 && mouseY >358 && mouseY < 464 && Emergency == false){
    elevatorFloor = 360;
  } //1th
  
  
  
  
}

void mouseCheck(int x, int y){
  
      if(x >5 && x < 410 && y >50 && y < 150){
    fill(243,243,21,63);
    rect(5,50,388,100);
    
  }  //4th
      if(x >5 && x < 410 && y >150 && y < 256){
    fill(243,243,21,63);
    rect(5,150,388,100);
  } //3th
      if(x >5 && x < 410 && y >256 && y < 353){
    fill(243,243,21,63);
    rect(5,256,388,100);
  }  //2th
      if(x >5 && x < 410 && y >358 && y < 464){
    fill(243,243,21,63);
    rect(5,358,388,100);
  } //1th
  

  
  if(x >450 && x < 750 && y >50 && y < 250){
    fill(243,243,21,63);
    rect(450, 50, 300, 200);
  } //emergency
  
  //open  buttons
  float disX = 500 - mouseX;
  float disY = 400 - mouseY;
  
  if(sqrt(sq(disX) + sq(disY)) < 75/2) {
    fill(243,243,21,63);
  ellipse(500,400,75,75);
  }
  //close button
  disX = 700 - mouseX;  
  if(sqrt(sq(disX) + sq(disY)) < 75/2) {
    fill(243,243,21,63);
    ellipse(700,400,75,75);
  }
  
  
}

