# Memory

## Array Shift

If you delete an element or insert an element in a dynamic array,
it is `O(n)` operation.

## Memory Reallocation

Sometimes memory reallocation happens: if you extend an array
beyond its capacity, it has to be copied to a new place.
The key optimization is this:
geometrically increase the available capacity upon each reallocation;
for example, by a factor of 2.

This is why appending to the end of a dynamic array has `O(n)` in the worst case.
But since it happens rarely, treat appending as `O(1)` (amortized complexity).
