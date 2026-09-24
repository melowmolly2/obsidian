# Search heuristics: estimates of distance to goal
- Often, even if we don't know the distance to the goal, we can estimate it
- This estimate is called a heuristic
- A heuristic is useful if:
	- $h(n) \sim h^*(n)$

- A heuristic function is:
	- A function that estimates how close a state is to a goal
	- Designed for a particular search problem
	- Examples: Manhattan distance, Euclidean distance for pathing
- The 8-puzzle problem: 
	- Number of misplaced tiles, or 
	- Total Manhattan distance 
- There can be many ways to evaluate 
- Evaluation functions may not be optimal
- How the evaluation function is chosen determines a lot of the results of heuristics search
# Beam search
- Similar to best first search
- However, expand only k nodes at the next level, not the whole expands

# A* Search
- uses evaluation function $f(n)=g(n)+h(n)$
	- $g(n)$: cost frrom initial node to node n
	- $h(n)$: estimated total cost of cheapest solution
 - Idea: preserve efficientcy of greedy search but avoid expanding path 
- A heuristic h is admissible (optimistic) if:
$$0\le h(n) \le h^*(n)$$
	where $h^*(n)$ is the true cost to a nearest goal
