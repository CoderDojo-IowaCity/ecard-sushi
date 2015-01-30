---
layout: post
permalink: /sushi/ecard/lesson3.html
title: Lesson 3
---
# Lesson 3
#### Making moves with animation

Now that you have your beloved's attention, let's knock it out of the park and make'em swoon... with animated hearts!

In the `images` folder, we have a file named [RHeartBig.png](images/RHeartBig.png).  What doesn't say "I love you" like an anatomically inaccurate depiction of a major organ, you say?  Nothing!  So let's use it.

Add the image to the canvas by adding these lines to the beginning of our javascript code:

```javascript
    var x1 = 0;
    var y1 = 200;
    img1 = new Image();
    img1.src = "images/RHeartBig.png";

```

:eyes: What?  It's not there... oh, yeah!  We forgot to draw it on the canvas!  Change your `draw()` function so it looks like this:

```javascript
    function draw(context) {
        var lingrad = context.createLinearGradient(0,0,0,400);
        lingrad.addColorStop(0, '#f57a86');
        lingrad.addColorStop(1, '#ffffff');
        context.fillStyle = lingrad;
        context.fillRect (0, 0, 600, 400);
        // Draw our heart
        context.drawImage(img1, x1, y1);
        // Write our message
        counter = counter + 1;
        if (counter > 100) {
            if (alpha < 100) alpha = alpha + 1;
            opacity = alpha / 100;
            context.font = "40px Times New Roman";
            context.fillStyle = "rgba(255,30,30," + opacity + "0)";
            context.textAlign = "center";
            context.fillText(myMessage, 300, 200);
        }
```

:eyes: Okay, now we're cooking with gas!  Are you starting to understand how our functions and variables are working together to create our eCard?  If you have any questions, think of ways to change the code to answer your questions (or use Google if you want to know about specifics of Javascript, jQuery, or HTML5).

What that you say?  There's no animation yet!?! Well, Mr./Ms. "I-can't-read-another-paragraph", try this on for size:

```javascript
    function draw(context) {
        var lingrad = context.createLinearGradient(0,0,0,400);
        lingrad.addColorStop(0, '#f57a86');
        lingrad.addColorStop(1, '#ffffff');
        context.fillStyle = lingrad;
        context.fillRect (0, 0, 600, 400);
        // Draw our heart
        y1 = y1 - 1;
        if (y1 < -300) y1 = 400;
        context.drawImage(img1, x1, y1);
        // Write our message
        counter = counter + 1;
        if (counter > 100) {
            if (alpha < 100) alpha = alpha + 1;
            opacity = alpha / 100;
            context.font = "40px Times New Roman";
            context.fillStyle = "rgba(255,30,30," + opacity + "0)";
            context.textAlign = "center";
            context.fillText(myMessage, 300, 200);
        }
```

What did we do?  Now everytime the `draw()` function is called, our `y1` variable decreases by 1.  This will move our heart upwards!

Why?

Well, `<canvas>` is a bit silly - it creates a grid of points and decides that the most important point, the "origin", is the top left corner.  That point is given the value (0,0): zero pixels up/down and zero pixels left/right.

Every other point is named according to it's grid distance from the origin.  So the point (5, 3) is 5 pixels to the right of the origin and 3 pixels down.  So far, so good?  If not, try drawing it out on a sheet of paper with a friend.  It'll soon make sense. ;-)

:cherries: Can you make the heart fall down?  How about make it go from left --> right?

:cherries: :cherries: BONUS: Can you make the heart move in a diagonal?

Repeat this step and add more hearts.  **Hint:** Make small hearts move slower and large hearts faster to give the illusion of depth to your card!  Also, put the `context.drawImage()` for the small hearts _before_ the big hearts so the small ones don't look like they're in front.

Now that you've fashioned Cupid's arrow, it's time to fire.  On to [Lesson 4](lesson4.md)!
