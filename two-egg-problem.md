# Two Egg Problem

**A building has 100 floors. One of the floors is the highest floor an egg can be dropped from without breaking.**

If an egg is dropped from above that floor, it will break. If it is dropped from that floor or below, it will be completely undamaged and you can drop the egg again.

Given two eggs, find the highest floor an egg can be dropped from without breaking, with as few drops as possible.

### Breakdown

What if we only had _one _egg? How could we find the correct floor?

Because we can't use the egg again if it breaks, we'd have to play it safe and drop the egg from _every _floor, starting at the bottom and working our way up. In the worst case, the egg won't break until the top floor, so we'd drop the egg 100 times.

What does having _two _eggs allow us to do differently?

Since we have two eggs, we can skip multiple floors at a time until the first egg breaks, keeping track of which floors we dropped it from. Once that egg breaks we can use the second egg to try every floor, starting on the last floor where the egg _didn't _break and ending on the floor below the one where it_did_break.

**How should we choose how many floors to skip with the first egg?**

What about trying a binary approach? We could drop the first egg halfway up the building at the 50th floor. If the egg doesn't break, we can try the 75th floor next. We keep going like this, dividing the problem in half at each step. As soon as the first egg breaks, we can start using our second egg on our \(now-hopefully narrow\) range of possible floors.

If we do that, what's the **worst case number of total drops?**

The worst case is that the highest floor an egg won't break from is floor 48 or 49. We'd drop the first egg from the 50th floor, and then we'd have to drop the second egg _from every floor _from 1 to 49, for a total of 50 drops. \(Even if the highest floor an egg won't break from is floor 48, we still won't know if it will break from floor 49 until we try.\)

**Can we do better than this binary approach?**

50 is probably too many floors to skip for the first drop. In the worst case, if the first egg breaks after a _small _number of drops, the second egg will break after a _large _number of drops. And if we went the _other _way and skipped **1 **floor every time, we'd have the _opposite _problem! What would the worst case floor be then?

The worst case would be floor 98 or 99—the first egg would drop a _large _number of times \(at every floor from 2-100 skipping one floor each time\) and the last egg would drop a _small _number of times \(only on floor 99\), for a total of 51 drops.

Can we balance this out? Is there some number between 50 and 1—the number of floors we'll skip with each drop of the first egg—where the first and second eggs would drop close to the _same _number of times in the worst case?

Yes, we could skip 10 floors each time. The worst case would again be floor 98 or 99, but we'd only drop the first egg 10 times and the second egg 9 times, for a total of **19 drops!**

**Is that the best we can do?**

Let's look at what happens with this strategy_each time the first egg doesn't break_.**How does the worst case total number of drops change?**

The worst case total number of drops _increases by one each time the first egg doesn't break_

For example, if the egg breaks on our first drop from the 10th floor, we may have to drop the second egg at each floor between 1 and 9 for a worst case of 10 total drops. But if the egg breaks when we skip to the _20th _floor we will have a worst case of _11 _total drops \(once for the 10th floor, once for the 20th, and all of the floors between 11 and 19\)!

**How can we keep the worst case number of drops from increasing each time the first egg doesn't break?**

Since the maximum number of drops increases by one each time we skip the _same amount of floors_, we could skip _one fewer floor _each time we drop the first egg!

But how do we choose how many floors to skip the _first _time?

Well, we know two things that can help us:

1. **We want to skip as few floors as possible the **_**first **_**time we drop an egg,**
   so if our first egg breaks right away we don't have a lot of floors to drop our second egg from.
2. **We **_**always **_**want to be able to reduce the number of floors we're skipping **_**by one**_**.**
   We don't want to get towards the top and not be able to skip any floors any more.

Now that we know this, can we figure out the ideal number of floors to skip the first time?

To be able to decrease the number of floors we skip by one _every time _we move up, and to minimize the number of floors we skip the first time, we want to end up skipping _just one floor at the very top_. Can we model this with an equation?

Let's say **n** is the number of floors we'll skip the first time, and we know 1 is the number of floors we'll skip last. Our equation will be:

```
n+(n−1)+(n−2)+…+1=100
```

How can we solve for **n**? Notice that we're summing every number from 1 to n.

The left side is atriangular series. Knowing this, can we simplify and solve the equation?

We know the left side reduces to:

$$(n2 + n) / 2$$

so we can plug that in:

$$(n2 + n) / 2 = 100$$

and we can rearrange to get a quadratic equation:

$$(n2 + n) / 2 - 200 = 0$$

which gives us **13.651**

We can't skip a fraction of a floor, so how many floors should we skip the first time? And what's our final **worst case total number of drops**?

