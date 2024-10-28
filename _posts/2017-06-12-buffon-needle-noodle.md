---
title: 'Buffon’s Needles and Noodles'
subtitle: 'A probability exercise leads to an exploration of circles and other shapes of constant width.'
date: 2017-06-12
permalink: /posts/2017/06/buffon-needle-noodle/
tags:
  - math
---


Here’s a fun little probability exercise, called Buffon’s Needle: Take a needle of length one unit, and drop it onto a field of parallel lines spaced one unit apart from each other. What is the probability that the needle crosses one of the lines?

![image](https://github.com/user-attachments/assets/8f78c7f8-0762-4e88-8588-17d0a6977616)


Imagine someone dropping a needle on its end. In a perfect world (the one we live in for most math and physics problems) one end of the needle hits the ground first (so it is balancing on its tip) and then the needle falls in a random direction.

We can simplify the problem a bit using symmetry. We can assume the needle falls to the right, eliminating half the possibilities. Also, the y-coordinate of the point does not matter because the board is the same along the y-axis, so we only need to look at the x-coordinate of the point. We can describe this by measuring distance from the closest line on the right which is some number between 0 and 1 which we will call d.

Now we have to determine the range of angles that the needle can fall towards and still intersect the line on the right. A graphic makes the right triangle that we need to use to solve the problem easier to see.

![image](https://github.com/user-attachments/assets/70d66863-d626-40bc-8c33-fe950f50cb5f)


$$\cos(\theta) = x
\theta = \arccos(x)$$

$2\theta$ is the size of the angle in which the needle can fall and intersect the line, and the total angle is 180 degrees or $\pi$ radians. The probability of crossing the line for each value of $x$ is therefore $\frac{2\arccos(x)}{\pi}$. Since we need to add these probabilities for each possible value of $x$, we integrate this function from 0 to 1.

$$\int_{0}^{1}\frac{2\arccos(x)}{\pi}$$

![image](https://github.com/user-attachments/assets/d0ab0704-371d-449f-ba41-ab9c12459ed1)

We can use the integral of \arccos(x), see proof here.

$$\int\arccos(x) = x \arccos(x) + \sqrt{1 - x^2} + c$$

Then with some very basic arithmetic (which I leave to the reader because it’s fairly unimportant), we find that

$$\frac{2\arccos(x)}{\pi} = \frac{2}{\pi}$$

So the probability that a needle of length one will intersect one of the lines is $\frac{2}{\pi}$ or about 0.64.

This property is commonly used as a neat demonstration to approximate $\pi$. Simply drop some needles (or other straight object, angel-hair pasta is a common choice) onto a field of evenly spaced lines and set the probability you get experimentally equal to $\frac{2}{\pi}$. If you would like to do this demonstration online, you can try here.

It tends to surprise students because we are only dealing with straight lines and straight needles, and $\pi$, usually associated with circles, shows up. However, doing the math makes it quite clear where the trigonometry comes in; it’s a result of the 360 degree angle the needle can fall in after touching the field.

The problem doesn’t need to have a needle of length 1. Once we get into longer lines, more than one intersection becomes possible and even probable, so we should stop talking about probability and start calling it “expected number of intersections”. Expected value is always additive so it grows linearly with length. So we can take dropping a needle of length 2 as having the same expected value as dropping 2 needles of length 1. Curves can be thought of as very short straight line segments arranged end to end, so we can use the same idea to determine the expected number of intersections for a curve. When you are working with curves, the problem in renamed Buffon’s noodle, but doesn’t change much outside of that.
The formula that becomes of interest therefore is: “expected intersections” =  $\frac{2}{\pi} \times l$ where $l$ is the length of the line or curve.

I got curious as to what would be the length of a curve that had exactly 1 or 2 expected intersections would be and quickly found that it would be $\frac{\pi}{2}$ and $\pi$. That second value isn’t surprising at all because it is the perimeter of a circle of diameter 1, which is guaranteed to intersect the field of parallel lines exactly twice.

![image](https://github.com/user-attachments/assets/cf51e964-b6c8-4e61-bfc4-3fd980f616b1)


Side note: is there a curve that guarantees exactly one intersection? (I don’t think there is, but I’m not positive) If not, is there a specific curve that gives the highest probability of exactly 1 intersection? (My guess is a straight line).

Initially, I thought that this might be a cool way to prove that a circle is the only constant-width shape, as any shape that would always intersect the field exactly twice would have to be a constant-width shape of width 1, and a circle was the only example I could think of. But when I looked it up, I saw that all I proved was that a constant-width shape of width 1 has to have a perimeter of \pi. There actually are constant-width shapes other than a circle. They are called Reuleaux polygons, and their boundaries are formed by  taking a polygon with an odd number of sides, centering a circle at each vertex, and using these to round off the sides.

For example, here’s a Reulaux triangle and pentagon (the shape itself is in red):

![image](https://github.com/user-attachments/assets/3a743004-037d-44d4-bf41-3faf27801ce2)


We can do this with any polygon with an odd number of sides (and make some pretty pictures too). Here’s a Reuleaux heptagon and nonagon:

![image](https://github.com/user-attachments/assets/e6d53e33-e2c9-4779-9b6e-c68d29aef5aa)


These are constant-width shapes, meaning they roll. For a more mathematical definition, every pair of parallel supporting lines (lines of the same slope that touch the perimeter of the shape) have the same Euclidean distance from each other regardless of orientation.

![image](https://github.com/user-attachments/assets/b2049f46-97f3-456b-aada-10daa2ddbb82)


Curves of constant width have many applications. They are surprisingly relevant to that old job interview question: Why are manhole covers round? Well, it’s because a circular manhole cover has constant width and therefore cannot fall into the sewer whereas a square one could be turned diagonally and accidentally dropped down there. A Reuleaux polygon would also serve for this purpose.

![image](https://github.com/user-attachments/assets/3fe3991e-1bc0-40f4-a0f2-65637985fe44)


Constant width is what enables circles to roll, so they can be used as wheels. So why don’t you see Reuleaux polygons being used as wheels? For most applications (such as cars and bikes), wheels need axles to turn around. In a Reuleaux polygon, the center point is not fixed as the object rolls but rather moves along a small circle within the shape. The movable axle required is quite the engineering challenge, and therefore impractical for most applications. However, ball bearings could theoretically be made by machining Reuleaux triangles instead of circles, and there would be no problem because no axle is required. It would even save a little metal because a Reuleaux triangle of width 1 has an area of about 0.705 as compared to a unit circle, which has an area of 0.785.

This gif shows the rotation of the central point of the Reuleaux triangle:

![image](https://github.com/user-attachments/assets/e9256169-3d63-4b03-8611-4e317e61585a)

This is quite the fun little problem and there is a ton more you can do with it mathematically than the usual approximating \pi which is rather cool in itself. How does the probability change if the lines are spaced further apart? If you have a grid rather than parallel lines? What about if you wanted to know the probability of having one intersection or two, or three, rather than the total expected value? How does that depend on the shape of the curve? Lots to explore here, even starting with the simple premise of needles and noodles.
