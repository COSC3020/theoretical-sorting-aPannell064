# Theoretical Sorting

A Computer Science researcher claims to have come up with a sorting algorithm
that can sort arbitrary elements in $O(n)$ time based on comparisons of two
elements at a time. This would be asymptotically faster than any known general
sorting algorithm. The algorithm itself is proprietary and will be sold by a
company.

How would you verify this claim? You may assume that you have access to a
black-box implementation of the sorting algorithm, i.e. you cannot examine the
source code, but you can use it to sort any list you like. Explain in detail
your method for investigating whether X is correct, including any expected
results you would get.

Also give a theoretical argument for why X could or could not be correct, based
on the complexity of the general sorting problem we covered in class.

Add your answers to this markdown file.

### Verifying X

There are two key aspects that I would want to verify. The first is that it
is in fact a sorting algorithm for arbitrary elements. The other is that it 
is in fact in $O(n)$ time, or at least "faster than any known general sorting 
algorithm."

To verify the first claim, I would write some property-based tests. This code would
generate a random list of integers and ensure that for any given list, (and all
of its permutations) the algorithm outputs a sorted list. The key part of this is that
all permutations must be returned sorted because the main concern is that a sorting algorithm
with linear time complexity wouldn't be able to possibly generate all orderings of a list. I 
would also want to verify that this works with other datatypes as well. We don't know how 
elements are being compared, but we know that two elements are being compared at a time. It's
possible that the comparison method wouldn't work as well with datatypes like strings or
a type of object that requires something like a lexicographic ordering that requires attributes
of an object to be compared based on a hierarchy. 

For the second claim, I would do several run time tests with varied input sizes. If the program really does scale linearly, the run time should increase proportionally to the input size for the most part. If n gets too large, the code could slow down due to lack of memory. Prior to that, I should be able to verify this claim by seeing if the relationship is roughly linear. 

### Theoretical Argument

I would find it highly unlikely that X is correct. This is because we know that it sorts "based on comparisons 
of two elements at a time." This makes it a comparison based algorithm. This means that, just like the example
covered in the theoretical bounds lecture, each comparison would have two outcomes, allowing us to represent the 
outcomes as a binary decision tree with the permutations being leaves. Because there are n! possible permutations 
of a given list there are at least n! leaves. A property of a binary tree is that if it has a number of leaves L, it 
has at least a height of $log_2(L) + 1$. This means that the decision tree has a height of at least $log_2(n!) + 1$, 
which is the same as $n \cdot log_2(n) + 1$ according to Sterling's approximation. As each level represents a comparison
in the tree, comparison based sorting algorithms have a lower bound complexity of $\Omega (n \cdot log(n))$. This complexity
represents the best possible algorithm to solve this solution. It would probably be safe to assume that this algorithm is
not better than the best possible solution. 

## Extra Help

"I certify that I have listed all sources used to complete this exercise, 
including the use of any Large Language Models. All of the work is my own, 
except where stated otherwise. I am aware that plagiarism carries severe 
penalties and that if plagiarism is suspected, charges may be filed against 
me without prior notice."
