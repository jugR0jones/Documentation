---
id: 04-for-loops
title: For Loops
tags:
  - Unity
  - Design
  - Patterns
  - Performance
---

## foreach loop

Ideal for Junior developers, foreach loops ensure a collection is iterated over correctly.

If an array is being iterated over, the compiler generates code that is similar to a for-loop. However, if the underlying collection is an IEnumerable, the compiler will allocate memory on the heap, and the iteration will use an iterator.

Iterators require more CPU resources and are thus slower.

## for Loops

For loops are quicker, and require fewer resources.

The most common method of using a for loop to iterate over a collection is:
```
for (int i=0; i < array.Length; i++)
{

} 
```

However, the terminating condition in this case is a check against the length of the array. With C#, this requires pushing the length of the array to the evaluation stack, and then comparing the length to the loop index.

A quicker way is to loop through the array backwards.
```
for(int i=array.Length-1; i >= 0; i--)
{

}
```
The length of the array is loaded once, at the start of the loop, and the loop index is compared against 0, an integer literal.