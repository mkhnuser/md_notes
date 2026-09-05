# Math

## Combinatorics

### Subsets

#### Iterative Solution

To generate subsets iteratively, let the output be = {{}}, and then consider generations:

        {};
        {}, {1};
        {}, {2}, {1}, {1, 2}.

#### Backtracking Solution

Maintain a pointer and increment it by one, accessing array elements.
