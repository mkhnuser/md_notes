# Memory

## Array Cyclic Shift

If you delete an element or insert an element in a dynamic array,
it is `O(n)` operation since a cyclic shift happens.

## Memory Reallocation

Sometimes memory reallocation happens: if you extend an array
beyond its capacity, it has to be copied to a new place since an array is a contiguous slice of data.

The key optimization is for reallocation is this:
geometrically increase the available capacity upon each reallocation;
for example, by a factor of 2.

This is why appending to the end of a dynamic array has `O(n)` in the worst case.
But since reallocation happens rarely, treat appending as `O(1)` (amortized complexity).
