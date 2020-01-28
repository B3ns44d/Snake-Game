# Snake Game Build By Using Only Javascript
[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)


In this github project, we will be creating a Simple Snake game in Javascript!. As it is made in JavaScript it can be run in a browser and works very well even with without any internet connection because their is no CDN Links used behind it, everything is built in by using Core JavaScript, 
  - HTML
  - CSS
  - JS


#Html Markup

First, start with creating a Canvas with appropriate height & width for snake game. This is what which is used to draw graphics using JavaScript. You can manipulate height & width according to you to increase size occupy for snake game

```html
<canvas id="stage" height="400" width="520"></canvas>
```
The id is a identifier for the canvas and should always be specified. We will use it to access the canvas later in javascript. After adding Canvas tag & you try to see that on browser you will see a blank page because canvas tag doesn't hold any property which will display on browser. You need to assign some properties by using CSS to display canvas tag on browser. Such as done below 

```css
canvas {
    border: 2px solid rgb(151, 149, 149);
    }
```

# Javascript

Now, make the snake game working. To control movement of snake we will use 4 keys such as. 
```javascript
Keyboard.Keymap = {
    37: 'left',
    38: 'up',
    39: 'right',
    40: 'down'
    };
```
 Here will see how the food for snake has built in x-axis & y-axis. 
 ```javascript
this.stage.food = {
    x: Math.round(Math.random() * (this.stage.width - this.stage.conf.cw) / this.stage.conf.cw), 
    y: Math.round(Math.random() * (this.stage.height - this.stage.conf.cw) / this.stage.conf.cw), 
};

// Logic of Snake food
if (nx == snake.stage.food.x && ny == snake.stage.food.y) {
  var tail = {x: nx, y: ny};
  snake.stage.score++;
  snake.initFood();
} else {
  var tail = snake.stage.length.pop();
  tail.x   = nx;
  tail.y   = ny;	
}
snake.stage.length.unshift(tail);

// Draw Food
this.drawCell(snake.stage.food.x, snake.stage.food.y);
 ```
 For getting current snake position either in x-axis or y-axis
```javascript
// Snake Position
var nx = snake.stage.length[0].x;
var ny = snake.stage.length[0].y;
```
And at last how the game will begin also how how it will get all values for game.
```javascript
/**
* Game Snake
*/
Game.Snake = function(elementId, conf) {

// Sets
var canvas   = document.getElementById(elementId);
var context  = canvas.getContext("2d");
var snake    = new Component.Snake(canvas, conf);
var gameDraw = new Game.Draw(context, snake);

// Game Interval
setInterval(function() {gameDraw.drawStage();}, snake.stage.conf.fps);
};
```
License
----

MIT


**Free Software, Hell Yeah!**
***Abdessamd Bensaad***
# demo

https://codepen.io/blackGamer/pen/GRgLVdJ
