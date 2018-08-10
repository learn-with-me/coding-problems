# Merging Meeting Times

## Description
Write a function for merging meeting times given everyone's schedules. It's an enterprise end-to-end scheduling solution, dog.

Your company built an in-house calendar tool called HiCal. You want to add a feature to see the times in a day when everyone is available.

## Details

To do this, you’ll need to know when any team is having a meeting. In HiCal, a meeting is stored as an object of a Meeting class with integer variables startTime and endTime. These integers represent the number of 30-minute blocks past 9:00am.
```
public class Meeting {

    private int startTime;
    private int endTime;

    public Meeting(int startTime, int endTime) {
        // number of 30 min blocks past 9:00 am
        this.startTime = startTime;
        this.endTime   = endTime;
    }

    public int getStartTime() {
        return startTime;
    }

    public void setStartTime(int startTime) {
        this.startTime = startTime;
    }

    public int getEndTime() {
        return endTime;
    }

    public void setEndTime(int endTime) {
        this.endTime = endTime;
    }
}
```

For example:
```
new Meeting(2, 3);  // meeting from 10:00 – 10:30 am
new Meeting(6, 9);  // meeting from 12:00 – 1:30 pm
```

Write a method `mergeRanges()` that takes a list of multiple meeting time ranges and returns a list of condensed ranges.

For example, given:
```
[Meeting(0, 1), Meeting(3, 5), Meeting(4, 8), Meeting(10, 12), Meeting(9, 10)]
```
your method would return:
```
[Meeting(0, 1), Meeting(3, 8), Meeting(9, 12)]
```

**Do not assume the meetings are in order.** The meeting times are coming from multiple teams.

**Write a solution that's efficient even when we can't put a nice upper bound on the numbers representing our time ranges.** Here we've simplified our times down to the number of 30-minute slots past 9:00 am. But we want the method to work even for very large numbers, like Unix timestamps. In any case, the spirit of the challenge is to merge meetings where startTime and endTime don't have an upper bound.

## Gotchas

Look at this case:
```
[Meeting(1, 2), Meeting(2, 3)]
```

These meetings should probably be merged, although they don't exactly "overlap"—they just "touch." Does your method do this?

Look at this case:
```
[Meeting(1, 5), Meeting(2, 3)]
```

Notice that although the second meeting starts later, it ends before the first meeting ends. Does your method correctly handle the case where a later meeting is "subsumed by" an earlier meeting?

Look at this case:
```
[Meeting(1, 10), Meeting(2, 6), Meeting(3, 5), Meeting(7, 9)]
```

Here all of our meetings should be merged together into just Meeting(1, 10). We need keep in mind that after we've merged the first two we're not done with the result—the result of that merge may itself need to be merged into other meetings as well.

Make sure that your method won't "leave out" the last meeting.

We can do this in O(n lg n) time.

## Complexity
O(n lg n) time and O(n) space.

Even though we only walk through our list of meetings once to merge them, we sort all the meetings first, giving us a runtime of O(n lg n). It's worth noting that if our input were sorted, we could skip the sort and do this in O(n) time!

We create a new list of merged meeting times. In the worst case, none of the meetings overlap, giving us a list identical to the input list. Thus we have a worst-case space cost of O(n).

## Bonus
* What if we did have an upper bound on the input values? Could we improve our runtime? Would it cost us memory?
* Could we do this "in place" on the input list and save some space? What are the pros and cons of doing this in place?
