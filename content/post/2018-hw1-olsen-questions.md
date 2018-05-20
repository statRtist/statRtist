---
{
  "title": "Introduction to Data Science - Homework 1 Questions",
  "subtitle": "Generic subtitle",
  "date": "2018-01-18",
  "slug": "itds-2018-hw1-olsen-questions"
}
---

This homework is designed to practice the skills we learned in up until Lecture 3: working with loops, conditions, functions, and the built-in Python data structures. Make sure to go through the lecture again in case you have any troubles.

**Note: You may not use higher-level library functions but should implement everything using functions, loops, and conditions.**

[(see also Solutions)]({{< ref "2018-hw1-olsen-solutions.md" >}})

## Problem 1 - Largest Element

Write a function that returns the largest element in a list.


## Problem 2 - Reverse List

Write function that reverses a list.


## Problem 3 - Combining List

Write a function that combines two lists by alternatingly taking elements, e.g. [a,b,c], [1,2,3] → [a,1,b,2,c,3].


## Problem 4 - Numbers to Digits

Write a function that takes a number and returns a list of its digits.


## Problem 5 - Sums

Write three functions that compute the sum of the numbers in a list: using a for-loop, a while-loop and recursion.

    
## Problem 6 - Fibonacchi Sequence

Write a function that takes a number n and an empty array that writes the first n numbers of the Fibonacchi Sequence into the empty array. Print the array. 

The Fibonnachi Sequnece where every number after the first two is the sum of the previous two numbers, i.e.,

1, 1, 2, 3, 5, 8, 13, 21, 34, 55, ...

## Problem 7 - Rainfall

Write a function called rainfall that reads a list of numbers representing daily rainfall amounts. The list may contain the number -999 indicating the end of the data of interest. Produce the average of the non-negative values in the list up to the first -999 (if it shows up). There may be negative numbers other than -999 in the list.

We provide you with several different test arrays, but your code should work with arbitrary arrays.


```python
rainfall_one = [16, 19, 22, 41, -999, 199, 254]
rainfall_two = [33, 24, 10, -2, -99, 0, 15, 82, -1325, 15]
rainfall_three = [2, 2, -999, 10]
rainfall_four = [-999, 2, 5, -19, 16]
rainfall_five = []
```

