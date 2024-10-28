Recently, I was introduced to a perpetual motion machine that appeared, at first glance, to be workable. In fact, at the end of nearly an hour of discussion with a physics teacher and some other students, I was convinced it would work. It relied on buoyancy to supply seemingly limitless, free kinetic energy. Many of the arguments against it could be easily be eliminated by making the machine larger or improving the quality of the parts. Alas, upon further examination I realized that in this machine (just like every perpetual motion machine) there is a fundamental flaw that cannot be overcome.

I talk about the specific machine later on, but much of my confusion about why the machine didn’t work stemmed from a misunderstanding of buoyancy. Buoyancy is not free energy at all, there is nothing magical about it. It is caused by the simple fact that water pressure increases with depth. This is best explained in a picture:

![image](https://github.com/user-attachments/assets/c276f979-e519-4c89-ac80-02d91f22fca1)

The buoyant force on the right “water ball” is exactly enough to suspend that mass of water, so it makes sense that the buoyant force is equal to the weight of the water displaced. The equation for buoyancy is:

 F_{buoyancy} = \rho g V 

where  \rho  is the mass density of the liquid,  g  is gravity, and  V  is the volume of the object. Remember, since water pressure is so crucial to buoyancy, it is important not to discount it when looking at buoyancy based “perpetual motion”.

Simple “Perpetual Motion” Machine that works based on buoyancy.

Before we get to the machine I was talking about earlier, let’s look at this simpler machine. (I don’t know whose original idea this was but I have seen several iterations of it online).

![image](https://github.com/user-attachments/assets/db7cf486-94ab-4067-b5ba-de36f5e44fe1)

The argument for why this machine rotates is that the ping-pong balls on the right will have a buoyant force acting on them, causing them to rise. The balls on the left only have a gravitational force acting on them and therefore fall. This causes the machine to spin counterclockwise. Looking at only the two sides of the conveyor belt, this argument is pretty convincing, it makes sense for the balls on the left to fall and the balls on the right to float. However, when you look at the top and bottom of the machine the argument starts to fall apart. Any kid who has pushed a rubber duck or bath toy underwater know that it takes work to force a low density object into the water. And that is exactly what is happening at the bottom left of this machine. In fact, we can even prove that the amount of work that the water does on a ping-pong ball in order to get it to the surface is exactly the same as the amount of work the ping-pong ball has to do to get from the air into the water. The net work is zero. This means that once the ping pong ball has entered the water, there is no work left over to actually rotate the machine.

 Work = Force \times Distance
 Work_{done \:by \:water \:on \:ball} = F_{buoyancy} \times height 
 F_{buoyancy} = \rho g V 
 Work_{done \:by \:water \:on \:ball} = \rho g V h 
 Work_{done \:by \:ball \:on \:water} = pressure \times V 
 pressure (at \:bottom) = \rho g h 
 Work_{done \:by \:ball \:on \:water} = \rho g V h 

More Complicated “Perpetual Motion” Machine:
Finally we arrive at the machine that inspired this write-up. It appeared in a footnote of Eric Rogers’ book, Physics for Inquiring Minds, and showing how it doesn’t work was left as a challenge for the reader.

![image](https://github.com/user-attachments/assets/e6efa6bd-9122-4729-a1a5-14032fd20a65)

This underwater machine is comprised of a conveyor belt with attached cups containing gas and a frictionless piston on top of the gas. Opposite cups have tubes connecting them so gas can pass between them. When a cup is on the left side, the piston is pulled away from the cup bottom by gravity, causing more gas to be pulled into the cup. When the cup is on the right side, the piston is pulled towards the cup bottom by gravity causing gas to be pushed out of the cup. Since the cups on the left side displace more water, they have a greater buoyant force acting on them than the cups on the right side. This buoyant force puts a torque on the conveyor belt and causes it to rotate clockwise.

Again, we will try and prove that the work done by the water while the cups are on the sides of the machine is equal to the work done on the water at the top and bottom of the machine, where the cups “cross-over”.

Since every cup has an opposite cup connected by a gas tube, it makes sense to think of the work done on a single pair of cups. First, let’s look at the work done by water to raise one left cup and lower the corresponding right cup.

 V_{1} - minimum \:volume \:of \:gas \:in \:cup
 V_{2} - maximum \:volume \:of \:gas \:in \:cup
 V = V_{2} - V_{1}
 Work_{done \:by \:water \:on \:pair \:of \:cups} = F_{net \:buoyancy} \times height
F_{net \:buoyancy} = \rho g V 
Work_{done \:by \:water \:on \:pair \:of \:cups} = \rho g V h 

This is exactly the same result as we got before (it just took a little more calculation because there were buoyant forces on both sides in this scenario).

Now we have to consider what happens as the cups make the transition from the left to right and vice versa. This diagram explains how the pistons move as the cup crosses over.

![image](https://github.com/user-attachments/assets/7fbd7681-7a58-495c-b8ec-ede516bd6eb8)


We can see that the bottom piston is moving outwards, against the force of water pressure, while the top piston is moving inwards, with the force of water pressure. It may seem logical that these two forces cancel out and the “crossing-over” has no effect on the rotation of the system. If this were true, we would actually have a perpetual motion machine. The cups would speed up every time they passed the straight sides of the machine and continue moving through the top and bottom. But before you worry about the ramifications of breaking the laws of thermodynamics, remember that you cannot forget pressure differences in buoyancy problems. Also, remember that pressure increases with depth. This means that the bottom piston is expanding in a higher pressure environment than the top piston is contracting. The work, therefore, does not cancel out. In order to transition from one side to another, the pistons must do some work on the water. Now all we have to do is show that the work the pistons do is equal to the work the water did on the cups.

 P_{1} - water \:pressure\:at \:top \:of \:machine
 P_{2} - water \:pressure\:at \:bottom \:of \:machine
A - cross-sectional \:area \:of \:piston 

![image](https://github.com/user-attachments/assets/1408f9f8-ff5b-472b-96b6-dfaca263d57f)

 F = pressure \times A 
 Work = Force \times distance 
 = pressure \times A \times l 
 = pressure \times V 
Work_{done\:by\:top\:piston} = P_{1} V
Work_{done\:by\:bottom\:piston} = P_{2} V
Work_{done\:by\:pair\:of\:pistons} = (P_{2} - P_{1}) V
 P_{2} - P_{1} = \rho g h
Work_{done\:by\:pair\:of\:pistons} = \rho g V h

So we have shown that the work done by the water in moving a set of cups to the top and bottom respectively is exactly cancelled by the work the pistons need to do to expand and contract while crossing from one side to the other. No matter how many cups you add or how streamlined you make the cups, the machine will not rotate forever.
