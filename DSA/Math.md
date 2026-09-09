# Math

## Combinatorics

### Subsets

#### Backtracking Solution

Maintain a pointer and increment it by one, accessing array elements.

#### Iterative Solution

To generate subsets iteratively, let the output be = {{}}, and then consider generations:

        {};
        {}, {1};
        {}, {2}, {1}, {1, 2}.

### Combinations

#### Backtracking Solution

Keep track of an event horizon:
you don't need to consider numbers which you've already visited.

### Permutations

#### Backtracking Solution

Once the first element is chosen, permute the rest.

#### Iterative Solution

Start with an empty list, then add the first element into every position, then the second, etc.
