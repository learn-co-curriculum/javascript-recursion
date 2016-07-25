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
######Photo Credits: Ron Knott/University of Surrey

For fun, try to figure out the next generation of rabbits on your own.

## Solving the Rabbits
If you're particularly mathematically inclined (or have already seen this problem), you may
recognize this as the [Fibonacci Numbers](http://oeis.org/A000045).<sup>[1]<sup>

As you may have figured out, the number of rabbits in any given year is the sum of the number
of rabbits in the previous two years. In math, we can write this as: `R(n) = R(n-1) + R(n-2)`,
`R(0) = 1`, and `R(1) = 1`, where `R(n)` is the number of rabbits in year `n`.

Wait a minute, if `R(n)` depends on `R(n-1)` and `R(n-2)`, how do we find `R(n)` in the first
place? Let's work out an example. Without looking back up at the chart, What's `R(4)`?

```
R(4) = R(4-1) + R(4-2)

R(4) = R(3) + R(2)

R(4) = R(3-1) + R(3-2) + R(2-1) + R(2-2)

R(4) = R(2) + R(1) + R(1) + R(0)
```

What we just did in that step is something called 'recurrence expansion.' We took the value
four, plugged it into the definition of the function, and then simplified the constants.
It seems a little silly, since we're still left with R in terms of 4 R's instead of 2.
Let's keep it up, though.

```
R(4) = R(2) + 1 + 1 + 1
```

There's our first major breakthrough. We can see from the definition of R that `R(0) = 1 = R(1)`
Since that's given, we can **always** replace `R(0)` and `R(1)` with `1`. Just a bit more to go!

```
R(4) = R(1) + R(0) + 3

R(4) = 1 + 1 + 3

R(4) = 5
```

**Ha**! We got it!

Now that you understand how how you can get an answer out of a recursive function, let's
write it up in code.

## The Code
One of the great things about recursive functions is that they tend to be more concise than their
purely iterative counterparts. Let's take a look at how we'd write our rabbit-counting function
without any recursion.
``` js
const R = n => {
  let a = 0
  let b = 1
  for(let i = 0; i < n; ++i){
   const temp = a
   a = a + b
   b = temp
  }
  return a
}
```

That's not particularly pretty. It works, but it isn't pretty. Let's take a look at the classic
recursive form.

``` js
const R = n => {
  return n <= 1 : R(n-1) + R(n-2)
}
```

Much nicer! Writing a function recursively can often lead to much cleaner and more explicit code.
If we looked at the iterative version, it would be more difficult to glean the underlying mathematical
formula than if we took a quick glance at the recursive one.

It's worth noting that there are two caveats to all of this talk of recursion. The first is that
writing recursive functions can be risky. If you aren't careful, it's possible to fall into an
infinite loop and blow through your stack space. The second is that despite being pretty, some recursive
functions have iterative or explicit versions that are faster by leaps and bounds. Our rabbit function
can take minutes, if not hours, for even relatively small values of n. There are ways to speed it up,
and if you're interested, there are some links in the resources section.

## Writing your own Recursive Functions
A recursive function has two main parts: the base case and the recursive case. The base case is a hard coded condition
where the program knows exactly what to do, and doesn't have to do any more calculations down that path. The recursive 
case is exactly what it sounds like. The recursive case


## Resources
* [Speeding up our rabbit counting function](http://rayhightower.com/blog/2014/04/12/recursion-and-memoization/)


## Citations
1: OEIS Foundation Inc. (2011), The On-Line Encyclopedia of Integer Sequences, http://oeis.org/A000045.
