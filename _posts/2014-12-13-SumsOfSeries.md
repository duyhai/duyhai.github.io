---
layout: post
title: Neat tricks to handle series
categories : [maths]
---

Though most of these tricks that I'm going to talk about are pretty well known, not many people consider their power until they really need them, but then, it is usually too late, since they are usually forgotten by that time. I wrote this post serves as a reminder for these people.

## Arithmetic series

The first one is actually pretty simple and easy to figure out on the spot, but I'm going to mention it anyway. When having to sum a series of numbers, each bigger than the previous one by a constant number, we have a simple formula to sum them up, instead of having to iterate through them. This essentially cuts down our running time from *O(n)* to *O(1)*, which is a huge improvement!

![The formula](/images/arithmeticsum.gif)

There is one prerequisite for this formula however. We have to know the number of elements we want to add up. If we know that number, we can also easily calculate the last element using the constant difference. Knowing the cardinality of the dataset we are working with is actually a pretty powerful knowledge and enables us to solve problems more efficiently in many situations.

## Geometric series

This one is not so obvious (at least for me) and may take a few extra seconds to understand its correctness even if we know the formula. 

![The formula](/images/geometricsum.png)

As we can see, we have to know the cardinality of our dataset here as well. This formula has another interesting property however. It works for infinite elements (only for *&#124;r&#124; < 1* though)! If we know basic calculus, we can easily verify this. The benefit here is just a constant factor: Originally we would have to use 2 operations for each element, but now, we just need to raise to the power of *n* and a few extra operations. The implementation of a power function in Math libraries is usually a bit faster though, sacrificing a bit of accuracy in return.

## Determining the values of a polynomial at *2n* points

If we have have 2 sets of points of *n* cardinality and for each element in the first set, there is an element in the second one, which equals to the first one times -1, then we can use the following formula to make our calculations a bit more efficient.

A(x) = a_0 + a_1&#42;x + ... + a_n&#42;x^n<br>
A(x) = A_e(x^2) + x&#42;A_o(x^2)<br>
A(-x) = A_e(x^2) - x&#42;A_o(x^2)

Where A_e is the part of A with the even numbered coefficients and A_o is the part with odd numbered ones. This trick only reduces our running time by a factor of 2, but this is still a very big improvement for large data sets.

## Conclusion

These techniques were probably not new to anyone, but people tend to forget these simple methods when all these problems can be solved by a mere for cycle. Remembering to use these tricks is vital if we want to work with large sets of numbers.