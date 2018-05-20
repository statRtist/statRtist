---
{
  "title": "Introduction to Data Science - Homework 1 Solutions",
  "subtitle": "Generic subtitle",
  "date": "2018-01-19",
  "slug": "itds-2018-hw1-olsen-solutions"
}
---

This homework is designed to practice the skills we learned in up until Lecture 3: working with loops, conditions, functions, and the built-in Python data structures. Make sure to go through the lecture again in case you have any troubles.

**Note: You may not use higher-level library functions but should implement everything using functions, loops, and conditions.**

[(see also Questions)]({{< ref "2018-hw1-olsen-questions.md" >}})

## Problem 1 - Largest Element

Write a function that returns the largest element in a list.


```python
def get_largest_element(my_list):
    if len(my_list)==0:
        return None
    my_max = my_list[0] # not efficient but works
    for element in my_list:
        if element > my_max:
            my_max = element
    return my_max
```

```python
get_largest_element([13, 25, 29, 17, 99, 133, -12, 0, 18])
```

    133



## Problem 2 - Reverse List

Write function that reverses a list.


```python
def reverse_list(my_list):
    if len(my_list)==0:
        return []
    output_list = []
    for i in range(len(my_list),0,-1):
        output_list.append(my_list[i-1])
    return output_list
```

```python
reverse_list([13, 25, 29, 17, 99, 133, -12, 0, 18])
```

    [18, 0, -12, 133, 99, 17, 29, 25, 13]



## Problem 3 - Combining List

Write a function that combines two lists by alternatingly taking elements, e.g. [a,b,c], [1,2,3] → [a,1,b,2,c,3].


```python
def combine_two_lists(my_list1, my_list2, add_extra=False):
    if len(my_list1)==0 and len(my_list2)==0:
        return []
    output_list = []
    list_length = min(len(my_list1),len(my_list2))
    for i in range(0,list_length,1):
        output_list.append(my_list1[i])
        output_list.append(my_list2[i])
        
    if add_extra:
        if len(my_list1) > list_length:
            for i in range(list_length + 1,len(my_list1),1):
                output_list.append(my_list1[i])
        if len(my_list2) > list_length:
            for i in range(list_length + 1,len(my_list2),1):
                output_list.append(my_list2[i])
    return output_list
```

```python
combine_two_lists(['a','b','c'], [1,2,3])
```

    ['a', 1, 'b', 2, 'c', 3]



## Problem 4 - Numbers to Digits

Write a function that takes a number and returns a list of its digits.


```python
def is_number(s):
    try:
        float(s)
        return True
    except ValueError:
        return False

def number_to_list(my_number):
    if not is_number(my_number):
        return None
    my_number_string = str(my_number).replace('.','')
    return [int(x) for x in my_number_string]
```

```python
number_to_list(3666)
```

    [3, 6, 6, 6]




```python
number_to_list(3666.56)
```

    [3, 6, 6, 6, 5, 6]



## Problem 5 - Sums

Write three functions that compute the sum of the numbers in a list: using a for-loop, a while-loop and recursion.


```python
def sum_list_for_loop(my_list):
    if len(my_list)==0:
        return None
    my_sum = 0
    for x in my_list:
        my_sum += x
    return my_sum

def sum_list_while_loop(my_list):
    if len(my_list)==0:
        return None
    my_sum = 0
    loop_i = 0
    while loop_i < len(my_list):
        my_sum += my_list[loop_i]
        loop_i += 1
    return my_sum

def sum_list_recursion(my_list):
    if len(my_list)==0:
        return None
    if len(my_list) == 1:
        return my_list[0]
    else:
        return my_list[0] + sum_list_recursion(my_list[1:])
```

```python
print(sum_list_for_loop([2,3,4]))
print(sum_list_while_loop([2,3,4]))
print(sum_list_recursion([2,3,4]))
```

    9
    9
    9
    

## Problem 6 - Fibonacchi Sequence

Write a function that takes a number n and an empty array that writes the first n numbers of the Fibonacchi Sequence into the empty array. Print the array. 

The Fibonnachi Sequnece where every number after the first two is the sum of the previous two numbers, i.e.,

1, 1, 2, 3, 5, 8, 13, 21, 34, 55, ...


```python
def fibonacchi_n_seq(n, should_print=False):
    if type(n)!=int or n<=0:
        return None
        
    output_list = []
    if n >= 1:
        output_list.append(1)
        if n >= 2:
            output_list.append(1)
            if n >= 3:    
                for i in range(2,n,1):
                    output_list.append(output_list[i-1] + output_list[i-2])
    if should_print: # directions were not clear if the function should print the list
        print(output_list)
    return output_list
```

```python
fibonacchi_n_seq(1,True)
fibonacchi_n_seq(2,True)
fibonacchi_n_seq(3,True)
fibonacchi_n_seq(10,True)
```

    [1]
    [1, 1]
    [1, 1, 2]
    [1, 1, 2, 3, 5, 8, 13, 21, 34, 55]
    




    [1, 1, 2, 3, 5, 8, 13, 21, 34, 55]



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

```python
def rainfall(rainfall_list):
    if len(rainfall_list)==0 or rainfall_list[0] == -999:
        return None # not sure what to return in this case
    if -999 in rainfall_list:
        filtered_list1 = rainfall_list[0:rainfall_list.index(-999)]
    else:
        filtered_list1 = rainfall_list
        
    filtered_list2 = [x for x in filtered_list1 if x >=0]
    if len(filtered_list2)==0:
        return None  # not sure what to return in this case
    return sum_list_for_loop(filtered_list2)/len(filtered_list2)
```

```python
# print the results for all the lists above here
rainfall(rainfall_one)
```

    24.5




```python
rainfall(rainfall_two)
```

    25.571428571428573




```python
rainfall(rainfall_three)
```

    2.0




```python
rainfall(rainfall_four)
```

```python
rainfall(rainfall_five)
```

```python
rainfall([-2,-2,-999,4])
```

