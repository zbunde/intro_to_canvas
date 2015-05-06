## Intro to Canvas

The goal of this exercise is to create and use functions to paint on a canvas.
Canvas is an html element that we can use to render graphs, draw game graphics, or animate things on the fly.

## Pre-work / Warmup
- Read "Drawing on Canvas", "The Canvas Element", and "Filling and stroking"
from chapter 16 in Eloquent Javascript.
[reading](http://eloquentjavascript.net/16_canvas.html)

- Read [Fibonacci Sequence](http://blog.javascriptroom.com/2013/01/10/fibonacci-an-introduction-to-recursion/)


### Setup

Clone this repository and open the file in google chrome. You can `open canvas.html` from the command line, or double click on the file in Finder.


### Iteration Zero: Poking Around, Drawing a Border: 9:45 - 10:15,

- Spend some time getting familiar with the files.
- We have an html file, a css file and a js file.
- Notice how the canvas is invisible to begin. It's markup looks like:

```
<canvas width="300" height="300" id="canvas"></canvas>

```

- First lets add a border so we can see what we are working on.
- In our canvas.js file there is a function called drawBorder.  
- You can uncomment each line in the js file as you go through the intro.

step 1: Find our canvas. We will use our ID given to the canvas to locate it.

```
var canvas = document.getElementById("canvas");

```
step 2: Set our context. Context is used to determine if we are using the canvas in a 2d/3d context. For this exercise we will use 2d. Every canvas has a drawing context, which is where all the drawing happens. Once we have located our <canvas> element in the DOM (by using document.getElementById() or any other method you like), you call its getContext() method.

[further reading](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D)

```
var context = canvas.getContext('2d');

```

step 3: Set our canvas size. This gives us a dynamic way to interact with our canvas. If we change our canvas dimensions later on, all of our later work will still function correctly.

```
var canvasSize = { x: canvas.width, y: canvas.height }
```
step 4: Time to draw our border: Since we are interacting with 2d we have x and y for points.
x: 0, y: 0 is the top left corner. If we want to draw a border around our canvas, we can use the strokeRect function. This takes 4 parameters. starting x, starting y, width, and height. Since we want our rectangle to fill our canvas we can use the size.x and size.y for our respective heights and widths.

- Notice how we can change the size of our canvas element but our border is drawn dynamically.

```
context.strokeRect(0,0, size.x, size.y);

```
step 5: All of it together:
```
function drawBorder(){
    var canvas = document.getElementById("canvas");
    var context = canvas.getContext('2d');
    var canvasSize = { x: canvas.width, y: canvas.height }
    context.strokeRect(0,0, canvasSize.x, canvasSize.y);
}

```
- now we just need to call our function. We can do script tags, and call drawBorder();.



### Iteration One: Drawing Rectangles 10:15 - 11:00

- Drawing the border we used the function strokeRect. In order to draw filled in rectangles we are going to use another function, fillRect. It takes similar parameters but instead of drawing a border it will fill in the entire rectangle.

- we can use fillStyle = 'color' to set the color for the drawing functions, make sure to set this before you stroke.

- Remember that our canvas starts at the top left with coordinates of 0,0. This means the bottom right coordinate is size.x, size.y.

-  When the canvas is clicked, draw a blue rectangle that takes up the top left 1/4th of the canvas.

-  To do this, define a function that paints a rectangle on a click event for the canvas.

- On Double Click on the canvas draw a red rectangle in the bottom right 1/4 of the canvas.

- Stretch: Do all of the painting dynamically based on the size of the canvas.

### Iteration Two: Drawing with Buttons 11:00 - 2:00

- When a user clicks one of the color buttons on the page, we paint a rectangle within the canvas, in a random location of a random size(make sure the size isn't so large that it covers the canvas.)

- remember that fillRect takes an X, a Y and then a width and height.

- Each click should add more rectangles to the canvas.

- When a user clicks "Clear Canvas" the canvas is cleared back to blank.

- Stretch: Add Circles, when a use hits a button it is either a circle our a square of a random size, location, and color.

- Stretch: Add incremental transparency to each rectangle so we are able to see the the ones behind each previous rectangle as they are painted.

### Iteration Three: Fibonacci Art 2:00 - 4:00

- get together in class at 2.

- we are going to draw the fibonacci sequence on a canvas, up to 14,  when a user presses the fibonacci button.

- there are three sides of this problem. the canvas / data visualization side, the solving of the actual equation and the handling of the user inputs.

- Solving Fibonacci:
    - Solving Fibonacci:
      - Solving Fibonacci:
        -  Solving Fibonacci:
            -  Solving Fibonacci:
                - Solving Fibonacci:
                    - Solving Fibonacci:
                        - Solving Fibonacci:
                          -  Solving Fibonacci:
                              -  Solving Fibonacci:
                                  - Solving Fibonacci:
                                      - Solving Fibonacci:
                                          - Solving Fibonacci:
                                            -  Solving Fibonacci:
                                                -  Solving Fibonacci:
                                                    - Solving Fibonacci:
                                                        - Solving Fibonacci:
                                                            - Solving Fibonacci:
                                                              -  Solving Fibonacci:
                                                                  -  Solving Fibonacci:
                                                                      - Solving Fibonacci:
                                                                          - Solving Fibonacci:
                                                                              - Solving Fibonacci:


`
```

function fib(x) {
    if (x === 0) {
        return 0;
    } else if (x === 1) {
        return 1;
    } else {
        return fib(x-1)+fib(x-2);
    }
}

```

- We are going to pass the row to our function, and then paint a square for each number.

- the first row will be 1, (or 0 your choice), so we would want to paint 1 square. the second would be 1, so we would paint 1 square, the third row would return 2 so we would fill in two squares.

- Canvas Side:
      - first we need to determine a pixel size to represent  a unit / digit.
      we can set this by dividing the height or width of our canvas by a number of our choosing.

      - we can then say that:

      ```
        pixel_size = canvas.width/100

       ```
       - now when we want to fill in a square we can use the starting x,y and then use the pixel_size as the width and height. fillRect(0,0,pixel_size, pixel_size) would fill the first square.

       - let's write a function called drawBlock that draws as individual block, that also takes a color:

       - make sure you have access to canvas and context in this function.

      ```
       function drawBlock(x, y, color){
           context.fillStyle = color
           context.fillRect(x, y, pixel_size, pixel_size);
      }

     ```

       - go into console in your browser.

       - write drawBlock(0,0 "red"), notice how it paints the first "pixel". Now
       drawBlock(1,0, "green"), notice how it paints it really close to the first one. We need to account for this change by multiplying our coordinates by the pixel_size in our drawBlock function.

       ```
       function drawBlock(x, y, color){
                context.fillStyle = color
                context.fillRect(x*pixel_size , y*pixel_size, pixel_size, pixel_size);
          }


       ```
       - Ok, again go into console:

       - write drawBlock(0,0 "red"), notice how it paints the first "pixel". Now
      drawBlock(1,0, "green"), it is set to the right of our first one and in a good position.

      - Now we are going to write a function takes three parameters.
      One is the row, the other is the length, and color.  if we wanted to paint the first row up to 5 and green, we would call:

        drawRow(0,5, "green")

      - We will print each pixel, up until we hit the rowLength, by using our drawBlock function and keeping the x value constant through each iteration.

      ```
      function drawRow(rowNumber, rowLength){
            for(i = 0; i < rowLength; i++)
                  {
                    drawBlock(rowNumber, i)
                  }
            }

      ```

       - Now we can write a drawFibonacci function that combines these things.
          - We can count across each row and paint each block up to its fibonacci number, using our drawRow function.
          - We will print up to the 14th number, starting at 1.
          -

       ```
       function drawFibonacci(){

         // counting on the canvas from left to right, rows 1-15.

         for(rowNumber = 1; rowNumber < 15; rowNumber++){

            // use our fib function to determine how many pixels down to paint.

            rowLength = fib(rowNumber);

            // use our drawRow function to print each individual block, for each row.

           drawRow(rowNumber, rowLength, "orange");


         }

       }

      ```

- Now we can make sure the function works by typing drawFibonacci() in our console.
- it it paints it, we are good.
- we could create an array of colors ["green", "red", "blue"] and pass a different color to each drawRow function in order to make each row a different color.
- now we just need to call this function when our fibonacci button is pressed. We might need to first clear out other painted shapes and rectangles, it is up to you.
- we can change the size of our canvas to be wide enough to look good with 15 rows.

#### Stretch
- Write a function that generates a random hexadecimal color, and use that for our randomly generated colors
