# Javascript Recursion

## Objectives

1. Understand what recursion is
2. Learn how to implement recursive functions

## Introduction

In this lab, we're going to learn the basics of recursion, one of the most invaluable tools
in any serious programmer's toolkit. Recursion is widely regarded as one of the
most mind-bending concepts in programming, and you should know that if you don't develop an
intuitive understanding of it immediately, you aren't alone.

## What is Recursion?
The academic and technical definition of recursion is that it's the act of self-reference.
In other words, recursion is what happens when something is defined in terms of itself.
One of my favorite examples of this is the use of recursive acroyms:
 * GNU: **G**NU's **N**ot **U**nix
 * PHP: **P**HP **H**ypertext **P**reprocessor
 * PiP: **P**IP **I**nstalls **P**ackages

As you can see, the acronym's explaination includes the acronym itself! This can be pretty
crazy to get your head around, but it'll come together soon.

## Wabbits!
Let's take a quick asside to chat about rabbits.

![If you're seeing this text, something bad has happened the the rabbit that used to be here. Please raise an issue.](http://i.giphy.com/4qlNG3rt5BC6I.gif)

For simplicity, let's say that these rabbits can reproduce twice a year, after their second
year of life. Also, these rabits are magic and live forever. They're mathematically
convenient rabbits, okay?

In year zero (we're programmers, remember), there is one pair of 
baby rabbits. Since they're too young, they don't produce any babies that year. In year one, 
those two rabbits have grown up and they're ready make a new pair of baby rabbits next year. 
In year two, they have a new pair of baby rabbits! We now have two pairs of rabbits. In year
three, the original pair of rabbits makes another pair. In year four, the original pair makes
another pair. On top of that, the rabbits born in year two are now old enough to make babies,
so they do. We now have a total of 5 pairs of bunnies on our hands.

If you're having trouble visualizing the situation, take a look at this graph:

![If you're seeing this text, the world may have been taken over by the exponentially growing rabbit population. Please raise an issue.](http://www.maths.surrey.ac.uk/hosted-sites/R.Knott/Fibonacci/fibrab.gif)

For fun, try to figure out the next generation of rabbits on your own.

## Solving the Rabbits
If you're particularly mathematically inclined (or have already seen this problem), you may 
recognize this as the [Fibonacci Numbers](http://oeis.org/A000045).

As you may have figured out, the number of rabbits in any given year is the sum of the number
of rabbits in the previous two years. In math, we can write this as: `R(n) = R(n-1) + R(n-2)`, `R(0) = 1`, and `R(1) = 1`,
where `R(n)` is the number of rabbits in year `n`.

Wait a minute, if `R(n)` depends on `R(n-1)` and `R(n-2)`, how do we find `R(n)` in the first
place? Let's work out an example. Without looking back up at the chart, What's `R(4)`?

```
R(4) = R(4-1) + R(4-2)

R(4) = R(3) + R(2)
```

So that was totally useless, right? Wrong! Let's keep expanding.

```
R(4) = R(3-1) + R(3-2) + R(2-1) + R(2-2)

R(4) = R(2) + R(1) + R(1) + R(0)
```

"See, I told you that was useless." - You

No! By the definition of `R`, we know that `R(1) = R(0) = 1`. Keep it up.

```
R(4) = R(2) + 1 + 1 + 1

R(4) = R(1) + R(0) + 3

R(4) = 1 + 1 + 3

R(4) = 5
```

**Ha**! We got it!

Now that you understand how how you can get an answer out of a recursive function, let's
write it up in code.

## The Code



## Resources
