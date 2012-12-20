Minimap
=======

A Minimap API with easy integration into any Canvas based game

Usage:
init
--------------
First, in the init of your game, init the minimap (the file has to be required, see require.js), for instance:
  var minimap = new Minimap({width: 100, height: 100, virtualWidth: 1440, virtualHeight: 1440, x: 690, y: 10, ctx: game.CTX, backgroundColor: "gray", pace: 50});

"width" and "height" attributes are the height and the width of the minimap on the screen. 
the virtualWidth / virtualHeight are the height and size of your world.
x and y are the position of your minimap on your canvas,
ctx is the canvas context,
pace is for the eventual blinky object on the minimap you use, at wich pace do you want them to blink.

creation of object types
--------------
then, you have to create objectTypes. The idea is to define the kind of object you want in your minimap, and their attributes (color, shape, blinkness..)
for instance:
  minimap.createType("block", "square", "green", false);
  minimap.createType("car", "round", "orange", false);
  minimap.createType("powerUp", "round", "red", true);
The first paramater is the id of the object, that you define. The second is the shape , "round" or "square", the third is the color,, and the last is a boolan that says if the object must blink or not.

draw
--------------
finally, in your gameloop, you must call this method for each object that has to be drawn.
  minimap.draw({type:"player", x:this.x, y:this.y, w:this.w, h:this.h, angle: this.angle})
the type refers to the one you created earlier
the position and size are world-scaled, you don't have to do the math (obviously)
the angle is in radian (radian = degree/(Math.PI*180) if you want to use degree).

Thank you, don't hesitate to communicate with me if you encounter any issue.
