# Class 01 Reading Notes: Data Structures and Algorithms

sources: links below, chatGPT
## Watch

- [Basic Recursion](https://www.youtube.com/watch?v=vPEJSJMg4jY)
- [Data Structures in 15 Minutes](https://www.youtube.com/watch?v=sVxBVvlnJsM)
- [Big O Explained](https://www.youtube.com/watch?v=v4cd1O4zkGw)

## Read

- [Basic Data Structures](https://towardsdatascience.com/8-common-data-structures-every-programmer-must-know-171acf6a1a42)
- [Why Big O](https://web.archive.org/web/20230207075759/https://triplebyte.com/blog/why-you-should-learn-big-o-and-stop-hacking-your-way-through-algorithms)

## What is 1 of the more important things you should consider when deciding which data structure is best suited to solve a particular problem?

- how well an operation scales / efficiency of the operations that will be performed on the data.
	- Different data structures excel in different types of operations, and choosing the right one can significantly impact the performance of your code.
- Big O: how time scales with respect to some input variables
	- different steps get added (e.g., add up the run times for each step)
	- drop constants - looking for things scale
	- different inputs => different variables
	- drop non-dominant terms
- 5 key data structures: 1) Linked lists, 2) Arrays, 3) Hash tables, 4) Stacks and queues, 5) Graphs and trees
## How can we ensure that we’ll avoid an infinite recursive call stack?

- always define a base case - condition under which the function stops calling itself
- progress towards base case - recursive call brings you closer to base case

## Things I want to know more about

- what are some examples of good base case for recursion?