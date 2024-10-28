---
title: 'A (Detailed) Look at the 4 Color Theorem'
subtitle: "A proof that went undone for 80 years we’ll go from maps, to planar graphs, to Kempe chains, to the final computer assisted solution."
date: 2019-07-24
permalink: /posts/2019/07/4-color-theorem/
tags:
  - math
--- 

## 2-Coloring Doodles
I was playing around with MS Paint recently and I ended up with a drawing that will probably look familiar to anyone who has ever idly messed around with MS Paint.
![image](https://github.com/user-attachments/assets/cd71913f-269c-4f51-a32c-68a313868c4d)


In addition to the nostalgia of remembering digital doodles from elementary school, I had another thought about this drawing. I wondered if it could always be colored with 2 colors “correctly” – such that colors only touched at corners (like a checkerboard). When I colored the drawings in using the Fill tool, the correct coloring naturally falls into place, but it is not entirely clear that should always happen. I could imagine a situation where it becomes unavoidable to color two adjacent regions with the same color (or to add a third color).

In fact, you will always be able to correctly color a pattern like this with 2 colors, and we can show it with a very simple inductive proof. We will induct on the number of lines in our pattern. If there is only one line splitting the plane, we (of course) can color the pattern by simply making one side black and one side white. So the “base case” works.

Now suppose we have a pattern made up of n lines and we have successfully 2-colored it. When we add another line, we can split the plane into 2 regions based on this line and arbitrarily designate one to be red and the other to be green. Leave the green region colored as it is, and invert the coloring in the red region (make black regions white and white regions black). Now along the new line no adjacent regions will have the same color, because one side’s coloring was inverted.

![image](https://github.com/user-attachments/assets/9f363f96-79ff-4bff-8c6e-a4b746ff497c)

So we generated a successful 2-coloring for n+1 lines from a coloring for n lines. Therefore (by induction), we can 2-color a pattern made up of any integer number of lines splitting the plane.

With a little work (try it!), we can generalize this result to patterns made up of closed shapes, curved lines, and lines that overlap themselves, like those shown below.

![image](https://github.com/user-attachments/assets/bd449567-44c5-4399-a075-a1fe91b48ef2)

The condition on 2-colorable “doodles” is that the lines can only overlap at single points. This means that no two lines can share a segment of non-zero length. In addition, only two lines can intersect at any single point.

![image](https://github.com/user-attachments/assets/4d7a7bd8-e21d-4d0e-87bf-dc46478c3e2a)

Moving onto Maps
Of course, the logical next question is: what if we made drawings (like those in coloring books) that did allow lines to have overlapping segments? How many colors would we need to color such a pattern “correctly” a.k.a. such that no two adjacent regions have the same color? We will call these patterns “maps” because cartographers usually try to preserve this property to prevent confusion between neighboring countries, states, provinces, or regions.

![image](https://github.com/user-attachments/assets/d3178447-0b3a-4c79-92fd-81959d14a72e)

A map of the United Stated colored with 7 colors. No adjacent states share a color. In this map, countries that touch at a corner also don’t share a color, but this is not a constraint for our purposes.
Source: Washington Post


By drawing a couple pictures, we can see that at minimum, we need 4 colors. This is because we can draw a map with 4 regions such that every region shares a side with all 3 of the others. This map clearly requires 4 colors. However, I was not able to draw a map with 5 regions such that every region shared a side with all 4 others.
![image](https://github.com/user-attachments/assets/941130ab-5a83-4de9-9fcf-673f13d9a70d)
A map that immediately requires 4 colors

But this by itself does not imply that all maps can be colored with 4 colors. It is easy to imagine a more intricate map where not being able to use the same color in two adjacent regions would eventually force a fifth or even sixth color.

![image](https://github.com/user-attachments/assets/44efb6b9-f009-498a-8900-ca7420fb8367)


If we 4 color the map on the left, and then add the encircling region, the map now requires 5 colors (as shown on the right). We can recolor the map on the right using 4 colors, but it is nontrivial to show that is always possible.
Maps → Graphs
This problem can be simplified somewhat by taking maps, which contain weird shapes of varying sizes, and translating them into “graphs” which only contain nodes and connecting edges. Every region will get a node, and if two regions share a side, then their nodes will be connected with an edge. This removes a lot of the complexity of the individual shapes involved in the maps, but preserves all the information we need to color them (because, based on the edges, we know which nodes cannot be the same color).
![image](https://github.com/user-attachments/assets/1987d427-82f0-4324-bcd3-d9a3089b6e3f)


Translating two maps that initially appear distinct into the same graph. This means that if one map can be 4-colored, so can the other. Notice that Graph 2 appears non-planar at first (lines cross) but since it can be “untangled” it is actually a planar graph.
All possible maps will lead to “planar” graphs, meaning that they can be drawn without the lines crossing (curved lines are allowed). Non-planar configurations do not correspond to valid maps, which makes a kind of sense if you consider the edges in a configuration to be analogous to regions.

Proof of the 6-Color theorem
Since the 4-color theorem is rather difficult to prove, let us start with the substantially easier (and weaker) 6-color theorem: no map requires more than 6 colors to ensure that no two adjacent regions have the same color.

We can apply theorems about planar graphs in order to prove the 6-colorability of all maps. One theorem is that every planar graph with v \geq 3 vertices and e edges, e \leq  3v - 6 (for a proof, see the Testing for Planarity section on this page). We can use this to prove that every planar configuration will have at least one vertex that connects to \leq 5 edges.

![image](https://github.com/user-attachments/assets/1a945ae4-662b-456f-9efc-55e7189b5931)

At least one of the vertices in any planar graph will look like one of the above vertices (shown in red). In other words, at least one vertex in a planar graph has less than or equal to 5 edges connected to it.
We will use proof by contradiction, so assume that every vertex in a graph connects to \geq 6 edges. Every edge connects to exactly 2 vertices, so e \geq \frac{6}{2}v. From the theorem above we know e \leq  3v - 6, so therefore 3v \leq  3v - 6 which is an obvious contradiction.

We can use proof by contradiction again to prove the 6-color theorem. Imagine there are some graphs that are not 6-colorable. If this is true, then there must be some minimal graph that is not 6-colorable. This graph – called a minimal criminal for “breaking the law” of 6-colorability – has the property that removing any edge will render it 6-colorable.

Suppose that this minimal criminal has a vertex A connected to 5 or fewer edges (it must, as we proved above). Let’s remove A and the edges connecting to it from our map entirely. The remaining graph has fewer edges than our minimal criminal, and therefore must be 6-colorable. So let us 6-color it. Now when we add A back into our map, there has to be a color (out of the six we are using) that is leftover, since A only connects to a maximum of 5 other countries. So we color A that leftover color and now our supposed “minimal criminal” is 6-colored. So no minimal criminal can exist and all graphs are 6-colorable.

![image](https://github.com/user-attachments/assets/41e60a80-9d17-4e8f-8dd1-cf6ec3f81af4)

Any “minimal criminal” planar graph requiring 7 colors can be recolored with 6 colors using this method. Therefore, any planar graph can be colored using 6 colors (you will never need 7 or more).

Attempting to Prove the 4-Color Theorem: A Proof of the 5-Color Theorem
The first attempted proof of the 4-color theorem appeared in 1879 by Alfred Kempe. The proof was similar to our proof of the 6-color theorem, but the cases where the node that was removed had 4 or 5 vertices had to be examined in more detail. Kempe came up with a method that involved exchanging sequences of alternating colors called Kempe chains. In order, to give you a better understanding of Kempe chains, I will explain how they can be used to prove the 5-color theorem.

From our proof of the 6-color theorem, we can realize that the only case that does not directly generalize to 5-colors is the case where the vertex we remove has 5 edges and connects to 5 differently colored vertices (since there will be no leftover color to use on the central vertex). So consider a vertex connected to 5 other vertices each with a distinct color. The method of Kempe chains (illustrated below) then allows for the 5 nodes surrounding our vertex to be colored with 4 colors, leaving the fifth for the central vertex.

![image](https://github.com/user-attachments/assets/897bdc19-30c5-4adf-bcf0-157068dcc678)

Recoloring a subgraph using the method of Kempe chains. The colors may not be in this order, but the basic idea is always the same.
Kempe cleverly used the method of Kempe chains to prove the 4-color theorem – or so he and the mathematical community thought. The proof appeared valid for 11 years until Percy John Heawood published a paper pointing out that in a particular subcase, Kempe’s method will not yield a 4-coloring (see here for more detail). Kempe tried to revise his proof, but was unable to do so. Note: The proof of the 5-color theorem using Kempe chains that we showed above is still valid.

Appel and Hakken’s Computer Assisted Proof
After Heawood refuted Kempe’s proof, mathematicians continued to try to prove (or disprove!) the 4-color theorem for over 80 years. Finally, in 1976, Kenneth Appel and Wolfgang Hakken published a paper called “Every Planar Map is Four Colorable”. Their eventual successful method ended up being similar to the proofs we discussed for the 6-color theorem and the 5-color theorem, only substantially more complicated.

The idea of the proof is to first come up with a set of configurations (which are subgraphs) such that every planar graph must contain at least one. This is called an unavoidable set. Then, it must be proved that every configuration in the set is reducible. This means that we can remove it from the larger graph, recolor the surrounding nodes with only 4 colors, and then reinsert the configuration colored with only 4 colors as well.

While this sounds complex due to the terminology, this is exactly what we did for the proof of the 5 and 6-color theorems. Our unavoidable set of configurations contained a single vertex with 1, 2, 3, 4, and 5 connecting edges.

![image](https://github.com/user-attachments/assets/b9110868-20cd-4d32-b800-dd502a249405)

Unavoidable set of configurations used in the proof of the 5 and 6-color theorems
Then we showed that each of these 5 configurations was reducible if we had 6-colors (just using common sense) or if we had 5-colors (using the method of Kempe chains). This proved there could be no minimal counterexample to the theorems, and therefore that the theorems were true.

Now the question becomes, how did Appel and Hakken come up with an unavoidable set of configurations where every element was reducible? They used something called the method of discharging. This involves treating a planar graph as an electrical network with charge assigned to the vertices such that the charges sum to a small positive value. Then the charges are redistributed in the graph via a set of discharging rules, which preserve the sum of the charges. The discharging rules are designed so that only certain subgraphs can “hold” positive charge. Since the charge is conserved, these subgraphs form a set of unavoidable configurations for the graph as a whole.

Appel and Hakken used a significant amount of trial and error to come up with discharging rules that resulted in a completely reducible set of unavoidable configurations. They prioritized having the unavoidable configurations be small, with a maximum ring size (the number of nodes in the boundary of the configuration) of 14. Their eventual discharging algorithm was simple enough to be implemented by hand (but still had 300+ rules) and yielded a set of 1,936 unavoidable configurations.

Each of these 1,936 unavoidable configurations had to be individually checked by a computer for reducibility. This took over 1,000 hours of computer time. And then, the 4-color theorem had finally been proven.

Appel and Hakken’s proof was the subject of some controversy because its extensive use of computational strength meant that it was not human-verifiable. Mathematicians worried that there could be some error in the software used to check for reducibility, which would render the proof invalid. Even the “human-verifiable” piece of the proof (the discharging procedure) was extremely complicated (400 pages of calculations!) and therefore impractical to actually check in its entirety. However, other software was later used to confirm the complete reducibility of the unavoidable set generated by Appel and Hakken. Smaller completely reducible unavoidable sets (as small as 633 configurations) have also been generated and checked. So the 4-color theorem has been proven beyond a doubt.

![image](https://github.com/user-attachments/assets/cd14ab7e-173d-4833-840f-e0d4a1f20f06)

Some of the configurations in the unavoidable set of 633 found by Robertson, N. et al.
Still, a level of dissatisfaction about the 4-color theorem remains in the mathematical community. There is lingering doubt that what Appel and Hakken did constitutes a “real” proof, since no human could ever completely understand every computation involved (there simply isn’t enough time in a single person’s life). Part of the problem is that the proof is rather ugly to the human eye: nearly 2,000 cases that have to be each checked individually?! The proofs of mathematical theorems are so often beautiful places of insight. By comparison, the complicated piece of calculation that is Appel and Hakken’s proof appears woefully inelegant.

However, there is something compelling about the fact that this simply-stated theorem remains unprovable without computer aid. Perhaps it suggests that we are reaching a point in mathematics where the complexity of our theorems and conjectures exceeds our personal computational abilities. And isn’t it exciting that we now have the tools (amazingly powerful computers) to take that next step? Computer assisted proofs are here to stay – examples include sphere packing, optimal Rubik’s cube solving, and coloring the Pythagorean triples – and our understanding of what a “proof” is will likely expand to accomodate.

Puzzles 🙂
It can be a rather fun time to try to “disprove” the 4-color theorem on your own by drawing some maps that are difficult to 4-color. People on StackExchange (1, 2, 3) thought the following maps were counterexamples to the 4-color theorem, can you color them successfully? (Note: You can copy the images into MS Paint and use the Fill Tool to color)

![image](https://github.com/user-attachments/assets/0a6a2e28-057f-4713-b993-54d8a2b5937f)

![image](https://github.com/user-attachments/assets/e492dc5b-c5b5-45ce-872d-c36a22837d3b)

![image](https://github.com/user-attachments/assets/b14345e8-0657-4ca7-a8b3-8eef5955116b)

If those weren’t enough of a challenge, try 4-coloring this puzzle. (Disclaimer: It took me 4 tries before I could do it)
![image](https://github.com/user-attachments/assets/89f82eef-db20-4992-9870-2fb764998e36)


Martin Gardner published this image as a “disproof” of the 4-Color Theorem in an April 1st edition of Scientific American (1975). William McGregor, the graph theorist who created the map, gave Gardner permission to use it in his little prank. Solution.
If you enjoy doing these kinds of puzzles (I certainly did) then check out the FourColor app (for iOS) which has a dozen or so more.

You might wonder if there is a general algorithm for 4-coloring a map, especially given the difficulty in proving that such a coloring even exists. Surprisingly there is, and it is even quadratic (a.k.a. pretty decent) in time-complexity! However, if you are given a planar graph, it is NP-complete to decide whether it is 3-colorable (not doable in polynomial time).

It seems appropriate that we can now use computer algorithms to 4-color maps, given that the (somewhat controversial) proof of their 4-colorability relies on the brute computing power of the modern era.
