
- **Record** - Data structure that stores subitems, often called fields, with a name associated to each subitem
- **Array** - Data Structure that stores an ordered list of items, where each items is directly accessible by a positional index
- **Linked List** - Data Structure that stores an ordered list of items in nodes, where each node stores data and has a pointer to the next node
- **Binary Tree** - Data Structure in which each node stores data and has up to two children
- **Hash Table** - Data Structure that stores unordered items by mapping each item to a location in array
- **Max-heap/min-heap** - Tree that maintains the simple property that a node's key is a less/greater than or equal to the node's children's keys
- **Graph** - Data Structure for representing connections among items, and consists of vertices connected by edges.
	- **Vertex**  - represents an item in a graph
	- **Edge** - represents a connections between two vertices in a graph


## Algorithms

An algorithm is a set of commands that must be followed for a computer to perform calculations or other problem solving operations. 

## Types of Algorithms

1. **Brute Force Algorithm** - A straightforward approach that exhaustively tries all possible solutions, suitable for small problem instances but may become impractical for larger ones due to high time complexity.
2. **Recursive Algorithm** - A method that breaks a problem into a smaller, similar subproblems and repeatedly applies itself to solve them until reaching a base case.
3. **Encryption Algorithm** - Utilized to transform data into a secure, unreadable form using cryptographic techniques ensuring confidentiality and privacy in digital communications and transactions.
4. **Backtracking Algorithms** - A trial-and-error technique used to explore potential solutions by undoing choices when they lead to an incorrect outcome, commonly employed in puzzles and optimization problems.
5. **Searching Algorithm** - Designed to find a specific target within a dataset, enabling efficient retrieval of information from sorted or unsorted collections.
6. **Sorting Algorithm** - Aimed at arranged elements in a specific order, like numerical or alphabetical, to enhance data organization and retrieval.
7. **Hashing Algorithm** - Converts data into fixed-sized hash value, enabling rapid data access and retrieval in hash tables, commonly used in databased and password storage.
8. **Divide & Conquer Algorithm** - Breaks complex problem into smaller subproblems, solves them independently and then combines their solution to address the original problem effectively.
9. **Greedy Algorithm** - Makes locally optimal choices at each step in the hope of finding a global optimum, useful for optimization problems but may not always lead to the best solution.
10. **Dynamic Programming Algorithm** - Stores and reuses intermediate results to avoid redundant computations, enhancing the efficiency of solving complex problems.
11. **Randomized Algorithm** - Utilizes randomness in its step to achieve a solution, often used in situations where an approximate or probabilistic answer suffices. 

## Factors of an Algorithm

- **Modularity** - Given a problem, it breaks it down into small-small submodules or steps
- **Correctness** - When given inputs, the desired outputs are produced
- **Maintainability** - Designed in a straightforward manner
- **Functionality** - Takes into account various logical steps to solve a problem
- **Robustness** - Ability to define the problem clearly
- **User-Friendly** - Easy to understand
- **Simplicity**
- **Extensibility** - Should be extensible if another person needs to use it

Characteristics of an Algorithm
- Well-defined Inputs
- Well-defined Outputs
- Unambiguity
- Finiteness
- Language Independent
- Effectiveness and Feasibility

## Data Flow Diagrams
- [Data Flow Diagram Tutorial](https://www.lucidchart.com/blog/data-flow-diagram-tutorial)

**Common Abstract Data Types**

| Abstract Data Type | Underlying Data Type           |
| ------------------ | ------------------------------ |
| List               | Array, Linked List             |
| Dynamic Array      | Array                          |
| Stack              | Linked List                    |
| Queue              | Linked List                    |
| Deque              | Linked List                    |
| Bag                | Array, Linked List             |
| Set                | Binary Search Tree, Hash Table |
| Priority Queue     | Heap                           |
| Dictionary         | Hash Table, BST                |


## Huffman Compression #study
Basic idea of compression is - given some quantity of bits, transform the data to use fewer bits.

Prior to compression, a character frequency table must be built for an input string. This table contains each distinct character from the input string and each character's number of occurrences

**Huffman Coding** - is a common compression technique that assigns fewer bits to frequent items, using a binary tree
- Each item is a leaf node. The pair of nodes yielding the lowest sum is found and merged into a new node formed with that sum

## Heuristics
Heuristic approach to algorithms will sacrifice optimization and accuracy for speed

**Knapsack Problem**
You need to pack a set of items, with given values and sizes into a container with maximum capacity. If the total size of the items exceeds the capacity, you can't pack them all. The problem is to choose a subset of the items of maximum total value that will fit in the container.
- If the weight of the nth item is more than the Knapsack capacity, then the item cannot cannot be included in the optimal solution.

**Self-Adjusting Heuristics**
Modifies the data structure based on how that DS is used. (Red-Black / AVL trees). By balancing the tree, you allow for faster data access
1. Starting with a list of numbers, search for the n-th number
2. Move that number to the front of the list
3. If another number is searched for it moves to the front of the list

Frequently searched for items get moved to the front so that they take fewer comparisons to find.

## Greedy Algorithms
A greedy algorithm solves a problem by assuming that the optimal choice at a given moment during the algorithm will also be the optimal choice overall.

**Fractional Knapsack Problem**
Similar to knapsack except that any fraction of an item can be selected

The optimal solution can be obtained by first sorting the items by their value-to-weight ratio, in descending order. The items are then added to the knapsack in that order, taking whole units of items until only a fraction of the next item is possible. The highest fraction of that item that will fit in the knapsack is taken, and the algorithm ends. 

## Dynamic Programming 
**Dynamic Programming** is a problem solving technique that splits a problem into smaller subproblems, computes, and stores solutions to subproblems in memory, and then uses the stored solutions to solve the larger problem. Example would be computing Fibonacci numbers or longest common substring

**Recursive Example**
```
FibonacciNumber(termIndex){
  if(termIndex == 0 )
	  return 0
  else if (termIndex == 1)
    return 1
  else
    return FibonacciNumber(termIndex - 1) + FibonacciNumber(termIndex - 2)
}
```

**Dynamic Programming Example**
```
FibonacciNumber(termIndex){
  if(termIndex == 0)
  return 0
  previous = 0
  current = 1
  i = 1
  while (i < termIndex) {
	  next = previous + current
	  previous = current
	  i = i + i
  }
  return current
}
```


**Longest Common Substring Snippet**
``` Python
def find_longest_common_substring(string_1, string_2):
  # build initial matrix with all 0s
  matrix = []
  for row in range(len(string_1)):
    a = []
    for col in range(len(string_2)):
      a.append(0)
    matrix.append(a)


  for row in range(len(string_1)):
    for col in range(len(string_2)):
      if string_1[row] == string_2[col]:
        upLeft = 0
        if row > 0 and col > 0:
          upLeft = matrix[row - 1][col - 1]
        matrix[row][col] = 1 + upLeft

      else:
        matrix[row][col] = 0
```

**Space-Saving Optimization**
Because dynamic programming techniques require solutions to subproblems are stored in memory and used to quickly find the solution to the full problem.

The code in the snippet above has a space complexity of *O(N* * M) because we iterate and store a matrix of n * m.

However, only the previous row is needed to compute to longest common substring - this would reduce the space complexity to *O(N)*
Consider the following change to the algorithm to provide this complexity reduction

```Python
``` Python
def find_longest_common_substring(string_1, string_2):
  # create a matrix with only one row
  matrix_row = [0] * len(string_2)

  max_value = 0
  max_value_row = 0
  
	for row in range(len(string_1)):
		up_left = 0
		for col in range(len(string_2)):
		  saved_current = matrix_row[col]
		  if str1[row] == str2[col]:
			matrix_row[col] = 1 + up_left	
			# Update the saved maximum value and row,
			# if appropriate.
			if matrix_row[col] > max_value:
				max_value = matrix_row[col]
				max_value_row = row
				else:
					matrix_row[col] = 0
					
				# Update the up_left variable
				up_left = saved_current
        
	# The longest common substring is the substring
	# in str1 from index max_value_row - max_value + 1, 
	# up to and including max_value_row.
	start_index = max_value_row - max_value + 1
	return str1[start_index : max_value_row + 1]
```