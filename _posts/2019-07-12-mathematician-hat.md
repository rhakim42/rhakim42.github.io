---
title: 'Mathematicians Many Hats'
date: 2019-07-12
permalink: /posts/2019/07/mathematician-hats/
tags:
  - math
---

A Relatively Easy Riddle:
Quite a while ago, I was introduced to a rather fun little brainteaser centering around colors of hats. The problem goes like this:

There is a line of 100 mathematicians, each positioned so that he can see all the hats in front of him but none of the hats behind him (nor his own hat). Each of the mathematicians is randomly assigned a colored hat, which is either red or blue. Note that there do not have to be exactly 50 of each color (since each mathematician’s hat color is independent of the others). Now the mathematicians are asked to guess the color of their own hat, starting from the back of the line and everyone can hear the guesses. Assuming that they are allowed to confer beforehand to discuss a strategy, what is the maximum number of mathematicians who can guess correctly?

![image](https://github.com/user-attachments/assets/a5df0f2b-a884-4560-83ac-ad425263ec6e)

An initial thought is that the first mathematician can say the color of the hat in front of them in order to relay that information to the second mathematician (counting from the back of the line). The second mathematician would guess correctly, and then the third mathematician would say the color of the hat in front of him. Continuing on like this ensures that at least 50 mathematicians get their hat color right (with an expected value of 75 correct guesses). However, they can actually do substantially better than that. In fact, with the correct strategy, all but one mathematician (the first) can guess their hat color correctly. Can you figure out how it should be done? For some hints, consider the following:

Each mathematician can see all of the hats in front of him, not just the one directly in front
There are only two possible hat colors – what property of an integer might we use?
Solution (to easy riddle)

![image](https://github.com/user-attachments/assets/e61e3d6e-c7df-4028-a969-b9edb77fe3de)

The solution is to decide on one color, let’s say red, to mean the first mathematician sees an even number of red hats, while the other color, blue, means they sees an odd number of red hats. Now the next mathematician can deduce his own hat color based on whether he sees an odd or even number of red hats (because he can see every hat the first mathematician saw except his own). He can make the decision based on this simple flowchart:


![image](https://github.com/user-attachments/assets/baabd8f5-f5ce-423d-8ed4-b1d6e6ef87de)


So the second mathematician can get his own hat color right. Now, the next mathematician (and every subsequent one) can figure out their hat color by analyzing the following formula:


![image](https://github.com/user-attachments/assets/920648dc-9671-4455-bbe6-f0198564b381)


Since every mathematician knows the parity (whether it is odd or even) of 3 numbers in this formula, they can figure out the parity of the 4th number. This means they know whether they are wearing 1 red hat or 0 red hats (meaning their hat is blue).
Now to Infinity!
Much more recently, at Caltech, I was introduced to variants of this riddle that make it significantly more interesting. The first involves replacing the line of 100 mathematicians with a countably infinite number of mathematicians. Now how many can guess their hat color right? This riddle requires making some strange assumptions, but it’s worth it because it dives into some really interesting math. So let’s assume that our mathematicians have infinite memory and can compare two infinite sequences in their “entirety” – obviously impossible for any human but our mathematicians are hardly human (is anyone who voluntarily puts themselves through a math PhD?).

An Aside About Equivalence Classes
Now to solve this problem we need something called equivalence classes. Equivalence classes are a partition of a set of objects (in this case, sequences of hat colors) such that every element in the equivalence class is “equal” to every other element. However, equality is not necessarily defined by our standard, intuitive, definition. It can be defined by any equivalence relation which preserves reflexivity, symmetry, and transitivity.

This seems confusing but can be clarified by a familiar example: fractions. One way of defining a fraction is as a pair of integers (a,b) such that b is non-zero. In more traditional notation, (a,b) means the same thing as   \frac{a}{b}. Now our equivalence relation on fractions will be as follows (the ~ indicates equivalence relation): (a_1, b_1) \sim (a_2, b_2)  if and only if a_1\times b_2 = a_2\times b_1 (the = sign represents standard equality). This makes sense because we can “cross-multiply” with fractions and preserve equality. Now that we have defined an equivalence relation, an example of an equivalence class for fractions would be all the fractions “equal” to (1, 2) such as (2, 4), (3, 6), (18,36), (510, 1020). These pairs of numbers are not really equal (we wouldn’t say (1,2) = (18, 36)) but with the correct equivalence relation defined, we can put them in the same equivalence class. Going into detail about the reflexivity, symmetry, and transitivity properties that any equivalence relation must have is a bit out of scope for this post, but I will give quick definitions here:

Reflexivity: a \sim a
Symmetry: if a \sim b then b \sim a
Transitivity: if a \sim b and b \sim c then a \sim c
If you would like, try to verify that our equivalence relation for fractions satisfies these three properties (it should be very easy to do).

Back to the Problem 🙂
Okay, now that we have some understanding of equivalence classes, we can solve the infinite case in a very similar manner to how we solved the 100 mathematician case.

What we want to do is reduce this infinite case to the finite case – which we know how to solve (we did it above). We can do this by dividing up the set of sequences of hat colors into equivalence classes using the following equivalence relation: two sequences are considered equal if they differ only at a finite number of positions. (If you would like, try to verify reflexivity, symmetry, transitivity on this equivalence relation). Now, the mathematicians must select a representative from each equivalence class. A representative is a single element from a particular equivalence class (any element). This element, by definition of equivalence classes, is “equal” to every other element in that equivalence class.

The set of hat sequences (in the case of infinite mathematicians) has infinite equivalence classes, each with infinite members, when equivalence is defined this way. To see why there are infinite equivalence classes, consider a sequence of all red. Then consider a sequence of alternating red and blue. Then consider a sequence that alternates 2 red and then 2 blue. Each of these could be a representative for a unique equivalence class, since it differs from the others in infinite positions. Continuing this pattern, we can generate infinite equivalence classes in this manner. To see why each equivalence class has infinite members, consider a representative sequence. Then consider a sequence that has the opposite color 1st hat but matches everywhere else. Then the sequence that has the opposite color 2nd hat (to the representative) but matches everywhere else. Since these sequences match the representative at all but 1 space (and 1 is finite) they are in the equivalence class of the representative. Continuing the pattern we can see that each equivalence class must have infinite elements.

In addition, every possible sequence of hat colors belongs to one and only one equivalence class. The transitivity of our equivalence relation ensures that a sequence cannot belong to more than one equivalence class. And if a sequence doesn’t belong to any existing equivalence class, we can make a new one for it (and all the infinite equivalent variants we just discussed above).

So in this new problem, the job of the mathematicians in their “conferral” period is to decide on a representative sequence from every equivalence class. A representative is just any element of the equivalence class, so in this case each representative is a particular infinite sequence of hat colors.

Once the mathematicians are arranged in a line, the first mathematician has to compare the sequence he sees with the set of representatives that were collectively decided on. Because of what we said earlier, the sequence of hat colors must fall into one and only one equivalence class. This means it differs from one (and only one) representative at a finite number of positions (it differs from the rest of the representatives at an infinite umber of positions). The first mathematician must figure out what this representative is and count the number of positions where the sequence differs from the representative. If this number is even, he’ll call out red (like before) and if it’s odd, he’ll call out blue. Every subsequent mathematician can now figure out their hat color using the same exact procedure as the finite case. However, instead of asking whether their hat is red or blue, they should ask whether their hat color differs from the representative sequence or not. From this (and from having collectively decided on a representative sequence beforehand), every mathematician except the first can guess their hat color correctly. Pretty cool!

Deaf Mathematicians and the Axiom of Choice
Now there is something weird about what we did in the first infinite case, which becomes clear when we consider another variant. In this variant, we also have an infinite line of mathematicians, but they’re all deaf. So no information is being carried forward when the mathematicians say their own hat color. Now, suppose the mathematicians create the set of representative sequences like we discussed they should do in the previous case. If they simply say the color that is at their position from the equivalent representative sequence, only a finite number of mathematicians will get their hat color wrong. This is because the sequence only differs from the representative at a finite number of positions (by our definition of equivalence).

So even in the case where each mathematician has no additional information from hearing the previous answers, they can guess their hat colors more accurately (only finite errors) than random guessing (almost definitely infinite errors). This doesn’t really make a lot of sense. No mathematician has any usable information about what their own hat color is, because no one who actually can see their hat has any mechanism of communicating with them. How can the mathematicians then do better than \frac{1}{2} getting the answer right?

The answer (or at least how the weirdness is introduced) is that implicit in our strategy for the mathematicians is the axiom of choice. The axiom of choice says something fairly simple: that for any non-empty set, we can choose one element from it. We need to make this assumption because our mathematicians need to collectively decide on a representative element from each equivalence class (set) of hat color sequences. The axiom of choice is key to our strategy in the infinite case. But this seems like a rather tame assumption – isn’t it obvious that if you have a box with things in it, you can reach in and grab one?


![image](https://github.com/user-attachments/assets/bd0c4d4e-ed9c-47dd-8bc6-7eb99c4c84d6)
Credit: xkcd

However, the axiom of choice tends to create some mathematical strangeness – weirder things can happen than mathematicians knowing their hat colors a little too well. For example, there is the Banach-Tarski Paradox, which states that the 3D solid unit ball can be decomposed into a finite number of pieces and then put back together (using only translations and rotations in space) into two identical copies of the original ball.

Despite, this kind of paradoxical result, ZFC (with AC (axiom of choice) is still generally the paradigm of “choice” for set theorists. So if our infinite mathematician solution still seems a bit suspect to you, just replace the mathematicians with some modern-day set theorists and you should be alright.
