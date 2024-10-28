---
title: 'Rainbows and Optics'
date: 2017-01-8
permalink: /posts/2017/01/rainbows-optics/
tags:
  - physics
  - math
---

In the optics unit of freshman year physics, we learned that any natural rainbow will form a circle 42^\circ wide, centered at the anti-solar point, like this:

![image](https://github.com/user-attachments/assets/ed5fed55-a0ef-4e7c-b874-333b334320ba)


This seems like a very cool phenomenon, because it means that the rainbow’s location is independent of both the size and location of the water droplets that form it. It is also pretty cool because this number, 42^\circ, can be derived from looking at the behavior of light inside a single droplet of water. Rainbows are typically formed out of thousands of drops of water, but we can understand something about them by examining just one.

So lets look at the path of sunlight through a raindrop, represented by the solid yellow line in this diagram.

![image](https://github.com/user-attachments/assets/bcb9dab4-b23f-45c1-8c72-5a4f933add66)


The diagram assumes total internal reflection (meaning all the light that enters the raindrop is reflected back out) which isn’t the case because some light does pass through the raindrop completely. However, only the internally reflected light forms the rainbow so we can safely ignore everything else. Also, notice how we don’t need to take into account the size of the raindrop.

![image](https://github.com/user-attachments/assets/93daadf1-30dc-4f27-9b6e-ffe012f9114d)


Looking at the quadrilateral highlighted in yellow, we get the equation  \delta + (360 - 2\alpha) + (\theta -\alpha) + (\theta - \alpha) = 360  because all the interior angles of a quadrilateral must add up to 360^\circ. This equation can be simplified down to  \delta = 4\alpha - 2\theta . The relationship between  \theta  and \alpha is dependent on the refraction of light when it travels from one medium to another (in this case from air into water). Therefore, we can use Snell’s Law to calculate \alpha in terms of  \theta  .

Snell’s Law states that  c_a \sin\theta = c_w \sin\alpha, where c_a is the speed of light in air and c_w is the speed of light in water. Using the index of refraction of water (n = \frac{c_a}{c_w}) simplifies the equation down to:

 \sin\theta = n\sin\alpha
\alpha = \arcsin(\frac{\sin\theta}{n})

Plugging back in for \delta:

\delta = 4(\arcsin(\frac{\sin\theta}{n})) - 2\theta 

Now we can graph \theta vs.  \delta  and see if we can understand why the rainbow forms where it does.

![image](https://github.com/user-attachments/assets/2fe76cb4-3b01-4505-9ed8-df118e0e4363)


We can see that the graph peaks at  \delta \approx 42  but how does that relate to the formation of the rainbow? Well, since the sun is so far away, light rays enter each droplet of water parallel to each other. This means that every value of  \theta  from 0^\circ up to 90^\circ has the same amount of incoming sunlight. However, the outgoing angle of the light ( \delta ) varies greatly with \theta for most of the graph which means that the light is scattered and therefore too diffuse to see. Near the peak of the graph, however,  \delta  barely changes with \theta. This means that the same amount of light is concentrated into a much narrower band. This is where you can see the rainbow.

![image](https://github.com/user-attachments/assets/9cc53b16-58d0-41c8-b616-24b56d275a91)


Here’s a visualization of what’s happening when you see a rainbow (the pictured cross section of the water droplet creates one point on the rainbow, the other cross sections and other droplets create the other points):

![image](https://github.com/user-attachments/assets/6e3f9856-fa39-4fc8-82a0-abad18cd2e21)


But what explains the different colors of the rainbow? You probably already know that white light is a combination of all colors of light, but how does a water droplet split these colors? Well, the different colors of light are a result of the different wavelengths of light. Red light has a longer wavelength than violet light, which allows it to travel faster in water. When I said the index of refraction for water was 1.333, that was actually just an approximation. In reality, red light has a slightly lower index of refraction of 1.331. Violet light, on the other hand, has a higher index of refraction of 1.340 (these values come from observations). If you use the exact values of n for the different colors of light when graphing, the graph of incoming vs. outgoing angles looks like this:

![image](https://github.com/user-attachments/assets/3d375266-3c68-43af-afb7-0cddb5b45772)


The difference in  \delta  between red and violet light at the peak of the graph is 2^\circ, which means that any rainbow you see will have a thickness of 2^\circ all the way around.

Just for fun (and in case graphs aren’t precise enough for you), lets try and determine  \delta  at the peak of the graph using algebraic methods. We know that at the maximum or peak of the graph \frac{d\delta}{d\theta} = 0 .

Using the equations from above:

 \delta = 4\alpha - 2\theta 
\frac{d\delta}{d\alpha}=4\frac{d\alpha}{d\theta}-2=0
\frac{d\alpha}{d\theta}=\frac{1}{2}

Add in Snell’s Law and take the derivative with respect to  \theta:

 c_a sin\theta = c_w sin\alpha
 \sin\theta = n\sin\alpha
 \cos\theta = n\cos\alpha\frac{d\alpha}{d\theta}
\frac{\cos\theta}{n\cos\alpha}=\frac{d\alpha}{d\theta}
\frac{\cos\theta}{n\cos\alpha} = \frac{1}{2}
\frac{\cos^2\theta}{n^2\cos^2\alpha} = \frac{1}{4}

To simplify further we need to use a trig identity to rewrite  \cos^2\theta :

\cos^2\theta + \sin^2\theta = 1  (Pythagorean Identity)
 \sin\theta = n\sin\alpha
 \sin^2\theta = n^2\sin^2\alpha
1- \sin^2\theta = 1-n^2\sin^2\alpha
\cos^2\theta=1-n^2\sin^2\alpha 

Plug back in:

\frac{1-n^2\sin^2\alpha}{n^2\cos^2\alpha}=\frac{1}{4}
\frac{1-n^2\sin^2\alpha}{1-\sin^2\alpha} = \frac{n^2}{4}

To make things a bit easier to write, use  x^2 = \sin^2\alpha:

\frac{1-n^2x^2}{1-x^2} = \frac{n^2}{4}

Cross-multiply:

4-4n^2x^2 = n^2-n^2x^2
4-n^2=3n^2x^2
x^2 =\frac{4-n^2}{3n^2}
x = \sqrt{\frac{4-n^2}{3n^2}}
\sin\alpha = \sqrt{\frac{4-n^2}{3n^2}}

Using  n = 1.333 , we get \alpha = 40.225.

We can use a very similar procedure to solve for \theta (this is left to the reader) or just plug this value of \alpha into Snell’s Law. Either way, we get \alpha = 40.225. Using these values in our original  \delta = 4\alpha - 2\theta , we get  \delta = 41.729.

We can do this same procedure with each of the individual colors of light to determine the exact location of a rainbow in the sky.

Another interesting implication of these calculations is that no two people ever see the same rainbow. Where you see the rainbow is dependent on where your eyes are in relation to the sun, so every person will see the rainbow in a slightly different location. So next time you see a rainbow, know that you are experiencing a unique aspect of nature’s beauty! 
