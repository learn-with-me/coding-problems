# In-Flight Entertainment System

## Description
You've built an inflight entertainment system with on-demand movie streaming.

## Details
Users on longer flights like to start a second movie right when their first one ends, but they complain that the plane usually lands before they can see the ending. So you're building a feature for choosing two movies whose total runtimes will equal the exact flight length.

Write a method that takes an integer flightLength (in minutes) and an array of integers movieLengths (in minutes) and returns a boolean indicating whether there are two numbers in movieLengths whose sum equals flightLength.

When building your method:

Assume your users will watch exactly two movies
Don't make your users watch the same movie twice
Optimize for runtime over memory

## Gotchas
We can do this in O(n) time, where n is the length of movieLengths.

Remember: your users shouldn't watch the same movie twice. Are you sure your method won’t give a false positive if the array has one element that is half flightLength?

## Reference

* [InterviewCake](https://www.interviewcake.com/question/java/inflight-entertainment)
