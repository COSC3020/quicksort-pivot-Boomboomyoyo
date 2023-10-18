[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=12432307&assignment_repo_type=AssignmentRepo)
# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

# Answer
I decided to go about this by considering the cases in which pivots could be considered.
G is a good pivot, B is a general bad pivot, L is a bad pivot on the left side, and R is a bad pivot on the right side.

Case 1: LLG or RRG, chance of $\frac{1}{2}*\frac{1}{4}*\frac{1}{2} = \frac{1}{16}$ per ordering. Order doesn't matter, and there are 3 orderings for a total of $\frac{1}{16}*3 = \frac{3}{16}$.
Median pivot will be bad if a good pivot and two bad pivots on one side of the sorted array is chosen.

Case 2: BBB, chance of $\frac{1}{2}*\frac{1}{2}*\frac{1}{2} = \frac{1}{8}$. Order doesn't matter, but there is only one ordering.
Median pivot will be bad if all pivot candidates are bad.

These are the only bad cases, as if GGG, GGB, or LGR are chosen, the median pivot will also be good.

Then the total chance of a bad pivot is, $\frac{3}{16}+\frac{1}{8} = \frac{5}{16}$, leaving the chance of finding a good pivot at $\frac{11}{16}$.

In percentage, that is a 68.75%, a markedly better chance of selecting a good pivot than the 50% of selecting a random element as a pivot.



# References
I kept making a simple algebra mistake, and conferred with Clayton. He helped me figure out which cases I was missing, and confirm my final answer. My mistake was I was doubling the LLG & RRG good cases, and I wasn't considering that order didn't matter.