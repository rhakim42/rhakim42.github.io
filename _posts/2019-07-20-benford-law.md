---
title: 'Putting #1 First – Deriving Benford’s Law'
date: 2019-07-20
permalink: /posts/2019/07/benford-law/
tags:
  - math
---
<font color="red">This text is red!</font>

A Motivating Game
Let’s play a game. I’m going to think of an integer, and now you have to guess the first digit. Is there any way you can do better than randomly choosing a digit 1-9? For psychological reasons, my number is probably going to start with 7 (it is my favorite digit), but let’s suppose I was choosing purely randomly.

For a hint, you might ask what is the range of integers that I’m choosing from. If I’m only choosing from the range 500 to 600, for example, your best option is a lot clearer. But all I’m willing to tell you is that I am choosing from 0 to n (exclusive), where n > 1. Quickly, you could figure out that if n is a power of 10 (i.e. 10, 100, or 1,000), then you can’t do any better than random guessing. Every digit appears as the first digit precisely \frac{1}{9} of the time (giving you an 11% chance of guessing correctly). But what if n was, for example, 3,000? The first thousand numbers have an even distribution of digits, but the next thousand (from 1,000 to 1,999) all start with one, and the rest (from 2,000 to 2,999) all start with two. Clearly, 1 or 2 is your optimal guess in this game (where n = 3,000).

You might be getting an inkling that the lower digits are your best bet for winning the game, and this is true. We can illustrate this by graphing the probability that 1 will be the first digit in a game as a function of n for that game. For comparison, we can make the same graph for the highest digit – 9. The red dashed line represents what the probability would be if every digit occurred with equal frequency (aka 0.11). Notice that the probability of 1 being the first digit is always \geq  0.11 while the probability of 9 being the first digit is always \leq  0.11.


![image](https://github.com/user-attachments/assets/5891d8b0-1936-4f59-b995-171c551ffd8c)


We can see the trend more clearly by graphing frequency (of being the first digit) vs. n for all 9 digits. I used a log scaling on the x axis to make the graph more evenly spaced (since dips/peaks occur at powers of 10).


![image](https://github.com/user-attachments/assets/6f81e73a-40fe-4853-b69b-d25fd6265adc)


So now you know that you should guess 1, but how likely are you to be correct using this strategy? Basically, we want to determine the average value of each of these curves. The standard strategy for doing this is to integrate the curve over a finite interval and then divide by the length of the interval. Using the interval 1 to 1ooo, we can find that the (approximate) probabilities for each digit are as shown below.


![image](https://github.com/user-attachments/assets/02fd42ed-76ca-40bf-b16a-3f0f0b1fb97f)


So if you guess 1, you have a 24% chance of being correct – this is more than twice as good as randomly choosing a number!
These values can maybe be thought of as the “frequency” that the digits show up as first digits in the infinite sequence of natural numbers. However, when I tried to do further research as to whether these probabilities actually show up anywhere in the real world, I found that there was an altogether different “first digit law” that shows up seemingly everywhere.

Benford’s Law
Benford’s law is named for physicist Frank Benford, who wrote a paper on it in 1938. It gives a distribution for first digits that applies to many different data sets and mathematical sequences. It states that the probability that some digit d will be the first digit is \log_{10} (1 + \frac{1}{d}).


![image](https://github.com/user-attachments/assets/65c3c141-9723-4832-ab46-7676b6c575e2)


The distribution dictated by Benford’s Law, similar to the first digit frequency we found for the natural numbers, indicates that lower first digits {1,2,3} are significantly more likely to occur than higher ones {7,8,9}. However, the distributions are not quite the same.


![image](https://github.com/user-attachments/assets/7db76612-1f82-4dcd-83d9-ddd77985aef7)


The reason Benford’s Law has a name, while our first distribution is stuck with the anonymous moniker “integration method”, is that the Benford distribution actually shows up in tons of data sets. Population data, stock prices, lengths of rivers, physical constants, the Fibonacci numbers. A fun exercise is to find some numerical data set (at least 100 entries) and check how closely the first digit distribution follows Benford. I’ve been on a Mathematica kick recently, so I chose GDP values from the 233 countries included in the CountryData tag. From the graph below, you can see the actual digit distribution pretty much follows what we would expect from Benford.

![image](https://github.com/user-attachments/assets/30a3160c-1812-4af9-862d-fe1c6eb6dc7f)

Explaining Benford’s Law with a Circular Slide Rule
So this begs the question: Why do so many datasets have first digits which follow this neat mathematical distribution? To answer this question, we can use the fact that the first digit of a number is encoded in it’s mantissa. What is a mantissa? The mantissa of a number n is the part after the decimal point of \log_{10} (n). We’ll use m(n) to denote the mantissa of n. For example, \log_{10} (283) = 2.45179 so m(283) is 0.45179.

![image](https://github.com/user-attachments/assets/0f26cc11-fee9-4a67-a4fb-428b535451b0)

The mantissa is unaffected by the addition of trailing zeros – so the mantissa of 2830 or 283,000,000 will also be 0.45179. Adding a trailing zero means you have to multiply by 10, meaning the characteristic of the logarithm will increase by 1, but the mantissa won’t change.

But what does it mean that the first digit is encoded in the mantissa? Well, basically, all numbers that start with 1 will have a mantissa between m(1) and m(2). Similarly, all numbers that start with 5 will have a mantissa that lies between m(5) and m(6). The intuitive reason for this is because the characteristic of the logarithm “absorbs” the less significant digits of the number – leaving the mantissa to carry the information about the more significant digits. So if two numbers share their most significant digit, their mantissae will be similar.

Now imagine a circular slide rule, which multiplies numbers by mechanically adding their logarithms. It utilizes the property that \log_{10}(ab) = \log_{10}(a) + \log_{10}(b). Let’s say we wanted to multiply 2 by 4. We would take \log_{10}(2)  which is 0.301 and add \log_{10}(4)  which is 0.602 to get 0.903. Then 10^{0.903} = 8 which is our answer. In order for this method to work, the logarithms of the numbers must be evenly spaced around the dial, not the numbers themselves (since we are adding the logarithms). We can use a circular slide rule to multiply numbers >10 as well, we just wrap around and adjust the position of the decimal point.

![image](https://github.com/user-attachments/assets/ae029f41-63be-4583-8bbe-43f71c408f7e)

A simple circular slide rule: The logarithms of the numbers are on the interior (red) dial and evenly spaced. The corresponding numbers on the outer (black) dial are therefore not evenly spaced.
Looking at the circular slide rule makes Benford’s Law a bit more intuitive. We can imagine it as a roulette wheel where multiplying several numbers is a “spin”. If we keep spinning the roulette wheel, we will land between 1 and 2 roughly 30% of the time, which is how often we expect to see 1 as a first digit according to Benford’s Law. More precisely, we expect to have 1 as a first digit when we land on the segment from \log_{10}(1) to $latex\log_{10}(2)$ and the overall circumference of the circle is 1. Generalizing, the probability of having a first digit d is \log_{10}(d+1) - \log_{10}(d) =  \log_{10} (\frac{d+1}{d}) =  \log_{10} (1 + \frac{1}{d}). This is, of course, Benford’s Law!

This analysis also gives us a better idea of what kinds of data sets will align with Benford. For example, exponential sequences are generated by repeated multiplication by a constant. As long as the mantissa of this constant doesn’t evenly divide the circle (like if the mantissa is irrational), this process will eventually cover the entire circle, implying the sequence will obey Benford’s Law. Since the irrationals greatly outnumber the rationals, nearly every exponential sequence will be Benford (this is a bit of a simplification, see here for a more complete explanation). An obvious exception to this “rule” is the sequence generated by multiplying by 10 every term. This explains why Benford’s Law applies to datasets that were created by exponential growth, like population data.

![image](https://github.com/user-attachments/assets/8a4eae53-b8a4-40a1-879a-bb3bee7a7cef)

One famous sequence that follows Benford’s Law exactly are the powers of two i.e. {2, 4, 8, 16, 32, 64, 128, 256, 512 …}. That this sequence is Benford follows from the fact that log(2) is irrational. The solid lines show the frequency of each first digit as a function of the number of terms in the series being considered. The dashed lines represent the frequency dictated by Benford’s law.
However, many other phenomena follow Benford’s Law as well, and this is most likely because they too can be thought of as being created by a series of multiplications. For example, stock prices typically scale by a constant each day. Or various variables (such as population, resources, and productivity) multiply together to create a nation’s GDP. There are no strict guidelines that govern whether a data set will follow Benford’s law, but the circular slide rule explanation gives us a clue.

Deriving Benford’s law with Scale Invariance
Another fascinating thing about the Benford distribution is that it is scale invariant. This means that if you take a data set that follows Benford’s Law and then multiply it by a constant, this data will still follow Benford’s Law. Since unit conversion is done by multiplying by a constant, this means a Benford dataset is Benford regardless of what the units are. This makes a sort of sense, units are an arbitrary choice and shouldn’t affect a digit distribution.

Benford’s distribution is actually the only distribution that has this property of scale invariance. We can see this pretty clearly by imagining the circular slide rule again. Pick a point on the outer rim to represent a number (it’s first digit will be determined by what segment it is in). To multiply this number by a constant we move it a fixed distance along the outer rim (the fixed distance is the \log_{10} of the constant).

Now, imagine instead of picking one point along the rim, we chose a distribution of points. Multiplying the distribution by a constant involves taking all those points and moving them all the same fixed distance along the rim. This is equivalent to rotating the disk around its center by some angle \theta. The only distribution that doesn’t change when this operation is applied (regardless of the value of \theta) is when points are uniformly distributed around the outer circle.

To illustrate this, imagine a distribution that is non-uniform and has an increased density of points in some region on the rim of the disk. Now when we rotate the disk, the increased density of points will now be in another region. Therefore, the distribution has changed and is consequently not scale invariant. We described above how a uniform distribution of points along the rim of the circular slide rule implies Benford’s Law. So we know that it is the only possible scale invariant distribution.

![image](https://github.com/user-attachments/assets/c87be169-9682-467a-88d4-03680c5804a5)

This image shows how a nonuniform distribution will necessarily change upon rotation. This means it cannot be scale invariant.
We can see an example of the scale invariance of Benford’s Law using the GDP data set from earlier. The data we graphed earlier was in US Dollars per year, but scale invariance implies that it shouldn’t change if we convert into other forms of currency such as euros or pesos. When we try it, we can see that the distribution remains quite similar.


![image](https://github.com/user-attachments/assets/7a9215a3-fd06-4c16-9cd5-a4a2ebf7e74c)


Benford’s Law is also the only distribution law that is base-invariant. This means that in base b, the probability that some digit d will be the first digit is \log_{b} (1 + \frac{1}{d}). Proving that Benford’s law is the only possible distribution that satisfies this constraint is quite a bit trickier than showing scale invariance, but it serves a similar purpose. It convinces us that this distribution function is inherent to our number system, not a quirk of how we choose to do things (because the base or units we choose to work in are largely arbitrary).

Generalizing to More Digits
Calling Benford’s Law the “first-digit law” is a bit of a misnomer. It also specifies a distribution function for the second, third, and nth digit in a number. The first digit simply exhibits the furthest “skew” from the uniform distribution that we intuitively expect. The generalization to multiple digits is quite easy to conceive if we keep our ideas about mantissae in mind. Earlier we talked about how all numbers that start with 3 will have a mantissa between m(3) and m(4). Similarly, all numbers that start with 13 (such as 13,000 or 139) will have a mantissa between m(13) and m(14).

We will assume that mantissas are evenly distributed, which is equivalent to saying numbers are uniformly distributed around our circular slide rule. So the probability of a number starting with 13 is \log_{10}(14)-\log_{10}(13) = \log_{10}(1+\frac{1}{13}). The probability of a number having a second digit of 3 is the sum of the probabilities that the number starts with 13, 23, 33, …, and 93. So the probability that our second digit will be 3 is \log_{10}(1+\frac{1}{13}) +  \log_{10}(1+\frac{1}{23}) + ... +  \log_{10}(1+\frac{1}{93}). This is approximately 0.104, so there is a 10.4% chance of having a 3 as the second digit in a dataset. If digits were distributed purely randomly there would be a 10% chance (remember we have 0 as a possible digit now). Repeating the process with all 10 digits, we find that the distribution of second digits is as seen below.

![image](https://github.com/user-attachments/assets/7260cc71-ab69-4b3b-a46a-7cbca18959d7)

We can see that this distribution is much more uniform than the one for first digits.
Of course, we can use the same procedure to generalize to 3+ digits and the distributions get flatter and flatter. Notice that instead of the (less general) formula, we used the assumption that the mantissae of numbers are uniformly distributed. In fact, this is exactly how mathematician Simon Newcomb described the same phenomena (actually earlier than Benford did!).

The law of probability of the occurrence of numbers is such that all mantissae of their logarithms are equally probable.
-Newcomb, American Journal of Mathematics (1881)

Applications
Benford’s Law has a fairly famous application in fraud detection. Most genuine financial data, such as tax returns or invoices, generally follows Benford’s law. However, fabricated data is unlikely to follow the law, due to humans natural bias towards uniform distributions. There tend to be too many numbers starting with 7,8, and 9 for example. Even if someone uses a random number generator, the distribution will be uniform rather than Benford because of the lack of exponential or multiplicative growth.

If a data set that should theoretically be Benford is not, it can raise a red flag for someone doing an audit. This cannot conclusively prove or disprove fraud, since often there are other factors causing an anomalous distribution, like a spending cap. However, it can raise suspicion for further investigation. In a 1993 case where Wayne James Nelson was accused of trying to defraud the state of Arizona of $2 million, check amounts that didn’t follow Benford’s Law was the initial clue that something wasn’t right.

Reflection
I’m sure Benford’s Law is of particular interest to forensic accountants (and I suppose, tax evading criminals trying to come up with some random numbers). As someone who belongs to neither of those groups (or at least doesn’t admit to it), I thought what was most interesting was to consider what data sets should conform to Benford’s Law.

The natural numbers don’t appear to, as I discussed at the beginning of this post. So Benford’s Law says something about real-world data, not just about numbers. The circular slide rule explanation exposes that exponential sequences and other multiplicative sequences should follow Benford’s Law. But does that apply to data sets of physical constants, or heights of mountains, or the masses of celestial bodies? All of these examples, and many more, have been observationally shown to follow Benford’s Law. Maybe the real discovery that Benford and Newcomb made isn’t just about digits, but about how multiplicative and exponential growth is inherent to so many unexpected corners of our universe.
