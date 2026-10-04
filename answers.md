# CMPS 2200 Assignment 3
## Answers

**Name:** Nahema Dumonteil


Place all written answers from `assignment-03.md` here for easier grading.


**1: Searching Unsorted Lists**

- **1b.** Work and span of `isearch` implementation
Work: iseatch uses iterate, so this meants it foes through the list one by one form left to right so for a list of n elements work is O(n)
Span: Since it uses iterate, and in iterate each step relies on the previous, it cannot be parallelized so the span stays the same at O(n)

- **1d.** Work and span of `rsearch` implementation
Work: Since we are using reduce, the work recurrence would be W(n) = 2W(n/2) + O(1) because we are splitting our list into 2 each time, and implementing reduce on both. At level 0, does 1*O(1) work. Level 1 -> 2 * O(1). Level 2 -> 4 * O(1), etc. Level I -> 2^i O(n). Summing it all up = O(n)
Span: Since we are splitting the list, and the 2 halves can work in parallel. Span S(n) = S(n/2) + O(1) since it does it is in parallel. 
So for all levels it is O(1). Summing O(1) for the hight of the tree which is log_2(n) = log_2(n) * O(1) = O(log(n)) for Span. 

- **1e.** Work and span of `rsearch` using `ureduce`
Work: Here we would have W(n) = W(n/3) + W(2n/3) + O(1). This leads to an an unbalanced tree. Since we have O(1), work at level 0 -> O(n). Level 1 -> 2 * O(1). Level 2 -> 4 * O(1), etc because even though it sunbalanced it still splits into 2 groups. Work end sup being O(n).
Span: Span ends up being O(log(n)) because of the same reasoing as 1d. Observation: because it is unbalanced it takes longer than a balanced tree, eventhough they behave the same asymptotically. 

**3: Parenthesis Matching**

- **3b.** Recurrences and Big-Oh solutions for `parens_match_iterative`
Since it is iterative it goes through each element in the list once so the work is O(n) fir a list with n elements.
The Span will be the same O(n) because it is iterative and iteration relies on the output of the previous step. 

- **3d.** Work and Span for `parens_match_scan`
Map:
Map applies paren_map to each element of a list of size n so it has work O(n). It has a Span of O(1) because if we have infinite processors, then paren_map can be abllied to all elements at the same time (not iterative, so we can parallelize), so it can all run in a single constant time step. 

Reduce:
Reduce divides the list until the base case and perfomes a function f all the way up, the total cumulative work is linear so it has wor of O(n). Since it is being divided, 2 branches could work at the same time but have to both be done before moving to the next level. A binary tree with n leaves has heiht of log_2(n) levels. The span turns out to be O(log(n))

Scan:
Scan goes through a whole list, so for a list of n elements, its work is O(n). Similar to Reduce, it looks like a balanced binary tree, so the Span is capped by the trees hight log_2(n) so the span is O(log(n))

Combining them together: Work is O(n) and Span is O(log(n))

- **3f.** Recurrences and Big-Oh solutions for `parens_match_dc_helper`
Assumng splitting and indexing run in constant time, the work recurrence would be W(n) = 2W(n/2) + O(1) because we are splitting our list into 2 each time, and implementing parens_match_dc_helper on both. At level 0, does 1*O(1) work. Level 1 -> 2 * O(1). Level 2 -> 4 * O(1), etc. Level I -> 2^i O(n). Summing it all up = O(n)

Span S(n) = S(n/2) + O(1) since it does it is in parallel. 
So for all levels it is O(1). Summing O(1) for the hight of the tree which is log_2(n) = log_2(n) * O(1) = O(log(n)) for Span. 