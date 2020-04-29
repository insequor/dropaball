# Falling Ball Exercise

This is the simple exercise to show how a ball falls from a certain height.
Physical accurrace is not the target

## Starting Point

start.html has the minimum start code to use P5.js in such an exercise

What is P5.js: Think it as a trusty helper. It knows things. In this specific case it knows how to organize the work in our application. It knows that it will call someone called "setup" when page is loaded. This is to give us a chance to tell him what we want to be done. Then it knows that it will call someone called "draw" periodically.

What is a function: See the function as a logical grouping of a set of commands. For example when someone tells you to "wash your face" what you do are a set of smaller actions:

* go to the bathroom
* turn on the water
* wash your hands first (it requires a number of smaller actions like take wet your hands, get the soap and rub your hands, then rub your hands with water to make them bubbly...)
* gather water in your hands
* splash the water to your face
* rub your face with your hands
* dry your hands and face

Instead of repeating all these instructions we just say "wash your face". It also enables us to use the same commands with different people where washing your face might require different set of instructions, like instead of going to the bathroom, go to the well and pull up some water.

## Drawing the ball

Ball is a round object, a circle. P5.js knows how to draw different [shapes](https://p5js.org/reference/#group-Shape). Circle is one of them.

To draw a circle we need to decide where we will draw it, and how bit it will be. First one is called _coordinates_ and second one is called _diameter_.

Try...

    circle(30, 30, 20);

Try changing the parameters and try to get an idea how each value affect the shape.

We shall see that (0, 0) is the top left corner of the page. And what we define is the center of the circle. We give the distance to the top left corner in horizontal and vertical direction (X and Y respectively).

> _circle_ is a function in p5js. This function requires three inputs, position and the diameter. Inputs are grouped within paranthesis and separated from each other with comma.

## Moving the circle

We draw a static circle, it does not move. But we want it to fall. Falling means, the distance to the top left coriner in vertical direction should increase each time we draw the circle. In order to do that we need to remember what was the previous position of the ball, and increase the distance as required. We use something called a _variable_ to remember the things. In this case let's give it a name:

    verticalDistance = 30;
    circle(30, verticalDistance, 20);
    verticalDistance = verticalDistance + 5;

This did not seem to work. Our circle is still not moving. That's because each time we draw the circle we first remember that the _verticalDistance_ is 30. Then we increment it. But next time we remember it again as 30. If we want to remember it properly, like what was it when we previously draw it, we should move the _verticalDistance_ outside the _draw_ function.

Try...

Now we see something moving. But there are couple of problems:

* Our circle is moving but it still leaves marks in previous places
* We only see it for a very short while. 

First problem is because p5js does not cleanup the page before drawing. We need to clean the background if we want to draw something on a clean surface each time. p5js has a function called _background_.

Try before doing any other drawing...

    background('blue');

Now it is better. But our ball drops quite fast. Let's reduce the speed a bit by reducing the increment before each draw.

Try different increment values...

Second problem is about our drawing area. P5js does not use all page to draw, only part of it. We did not tell it how big a drawing area we want to it is using something default for now. This kind of instructions are usually given once, before we start drawing. P5js knows a function called _setup_ and if we use it we can give setup instructions like the canvas size.

Try...

## Hitting the ground

We want our ball to fall and stop when it hits the ground. First we need to draw a ground. Simplest ground would be a straight horizontal line. If we check the available shape functions we can find the line

Try ...

    line(0, 400, 640, 400);

Our canvas is 480 in height, we put the ground at 400 units away from the top. Below our line we still see the blue color which is confusing. Perhaps we can just fill that area. Instead of a line we can use a rectangle to mark the ground

Try...
    rect(0, 400, 640, 80);

This gave us a white ground. We want to change the color. If we check the [color functions](https://p5js.org/reference/#group-Color) we will see _color_ function and _fill_ function.

TODO: Explain the usage of fill for ball and ground. Also talk about stroke color.

