# Free Rotation Problem - Solution

## Gotchas
We can get O(\lg{n})O(lgn) time.

## Breakdown
The array is mostly ordered. We should exploit that fact.

What's a common algorithm that takes advantage of the fact that an array is sorted to find an item efficiently?

Binary search! ↴ We can write an adapted version of binary search for this.

In each iteration of our binary search, ↴ how do we know if the rotation point is to our left or to our right?

Try drawing out an example array!
```
  [ "k","v","a","b","c","d","e","g","i" ]
             ^
```
If our "current guess" is the middle item, which is 'c' in this case, is the rotation point to the left or to the right? How do we know?

Notice that every item to the right of our rotation point is always alphabetically before the first item in the array.

So the rotation point is to our left if the current item is less than the first item. Else it's to our right.

## Solution
This is a modified version of binary search. ↴ At each iteration, we go right if the item we're looking at is greater than the first item and we go left if the item we're looking at is less than the first item.

We keep track of the lower and upper bounds on the rotation point, calling them floorIndex and ceilingIndex (initially we called them "floor" and "ceiling," but because we didn't imply the type in the name we got confused and created bugs). When floorIndex and ceilingIndex are directly next to each other, we know the floor is the last item we added before starting from the beginning of the dictionary, and the ceiling is the first item we added after.
```
  public static int findRotationPoint(String[] words) {
    final String firstWord = words[0];

    int floorIndex = 0;
    int ceilingIndex = words.length - 1;

    while (floorIndex < ceilingIndex) {

        // guess a point halfway between floor and ceiling
        int guessIndex = floorIndex + ((ceilingIndex - floorIndex) / 2);

        // if guess comes after first word or is the first word
        if (words[guessIndex].compareTo(firstWord) >= 0) {
            // go right
            floorIndex = guessIndex;
        } else {
            // go left
            ceilingIndex = guessIndex;
        }

        // if floor and ceiling have converged
        if (floorIndex + 1 == ceilingIndex) {

            // between floor and ceiling is where we flipped to the beginning
            // so ceiling is alphabetically first
            break;
        }
    }

    return ceilingIndex;
}
```

## Complexity
Each time we go through the while loop, we cut our range of indices in half, just like binary search. So we have O(\lg{n})O(lgn) loop iterations.

In each loop iteration, we do some arithmetic and a string comparison. The arithmetic is constant time, but the string comparison requires looking at characters in both words—every character in the worst case. Here, we'll assume our word lengths are bounded by some constant so we'll say the string comparison takes constant time.
```
The longest word in English is pneumonoultramicroscopicsilicovolcanoconiosis, a medical term. It's 45 letters long.
```
Putting everything together, we do O(\lg{n})O(lgn) iterations, and each iteration is O(1)O(1) time. So our time complexity is O(\lg{n})O(lgn).
```
Some languages—like German, Russian, and Dutch—can have arbitrarily long words, so we might want to factor the length of the words into our runtime. We could say the length of the words is \ellℓ, each string comparison takes O(\ell)O(ℓ) time, and the whole algorithm takes O(\ell*\lg{n})O(ℓ∗lgn) time.
```
We use O(1)O(1) space to store the first word and the floor and ceiling indices.

## Bonus
This method assumes that the array is rotated. If it isn't, what index will it return? How can we fix our method to return 0 for an unrotated array?

## What we learned
The answer was a modified version of binary search.

This is a great example of the difference between "knowing" something and knowing something. You might have seen binary search before, but that doesn't help you much unless you've learned the lessons of binary search.

**Binary search teaches us that when an array is sorted or mostly sorted:**

* The value at a given index tells us a lot about what's to the left and what's to the right.
* We don't have to look at every item in the array. By inspecting the middle item, we can "rule out" half of the array.
* We can use this approach over and over, cutting the problem in half until we have the answer. This is sometimes called "divide and conquer."

So whenever you know an array is sorted or almost sorted, think about these lessons from binary search and see if they apply.
