# Triangular Series

A **triangular series **is a series of numbers where each number could be the row of an equilateral triangle.

So 1, 2, 3, 4, 5 is a triangular series, because you could stack the numbers like this:

![](https://www.interviewcake.com/images/svgs/triangular_series__triangle_of_stacked_circles.svg?bust=202 "Rows of 1, 2, 3, 4, and 5 circles to show how numbers in a triangular series can be stacked to form a triangle.")

Their sum is 15, which makes 15 a **triangular number**.

A triangular series _always _starts with 1 and increases by 1 with each number.

Since the only thing that changes in triangular series is the value of the highest number, it’s helpful to give that a name. Let’s call it **n**.

```
# n is 8
1, 2, 3, 4, 5, 6, 7, 8
```

Triangular series are nice because no matter how largennis, it’s always easy to find the total sum of all the numbers.

Take the example above. Notice that if we add the first and last numbers together, and then add the second and second-to-last numbers together, they have the same sum! This happens with _every _pair of numbers until we reach the middle. If we add up all the pairs of numbers, we get:

```
1 + 8 = 9
2 + 7 = 9
3 + 6 = 9
4 + 5 = 9
```

This is true for_every triangular series_:

1. **Pairs of numbers **on each side will always **add up to the same value**.
2. That value will always be **1 more than the series’ n**.

This gives us a pattern. Each pair's sum is `n+1`, and there are `n/2` ​pairs. So our total sum is:

$$(n+1) ∗ n/2
​	$$

Or:

$$(n2 + n)/2$$

Ok, but does this work with triangular series with an _odd _number of elements? Yes. Let's say `n = 5`. So if we calculate the sum by hand:

```
1+2+3+4+5 = 15
```

And if we use the formula, we get the same answer:

$$(5 * 5 + 5)/2 = 15$$

One more thing:

**What if we know **_**the total sum**_**, but we **_**don't **_**know the value of n?**

Let’s say we have:

```
1 + 2 + 3 + … + (n−2) + (n−1) + n = 78
```

No problem. We just use our formula and set it equal to the sum!

$$(n2 + n)/2 = 78$$

Now, we can rearrange our equation to get a _quadratic equation _\(remember those?\)

$$n2 + n = 156$$

$$n2 + n − 156 = 0$$

Here's the quadratic formula:

$$(−b ± Sqrt(b2 − 4ac)/2a)$$

If you don't really remember how to use it, that's cool. You can just use an online calculator. We don't judge.

Taking the positive solution, we get `n = 12`.

So for a triangular series, remember—the total sum is:

$$(n2 + n)/2$$

  


