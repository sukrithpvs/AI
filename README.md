
# Graph Search Algorithms

This repository implements various search algorithms on a given graph, starting from node `S` and ending at node `G`. Each algorithm finds the best path from `S` to `G` based on different strategies. The graph and heuristic values are hard-coded, but you can modify them as needed.

## Graph Structure

The graph used in all algorithms:

```
graph = {
    'S': {'A': 1, 'B': 2, 'C': 5},
    'A': {'D': 3, 'S': 1, 'B': 1},
    'B': {'A': 1, 'S': 2},
    'C': {'E': 4, 'S': 5},
    'D': {'A': 3, 'G': 2},
    'E': {'C': 4},
    'G': {'D': 2}
}
```

The heuristic values for each node:

```
heuristic = {
    'S': 6,
    'A': 4,
    'B': 3,
    'C': 5,
    'D': 1,
    'E': 3,
    'G': 0
}
```

## Algorithms and Expected Outputs

### 1. **British Museum Search**
- **Description:** This is a brute-force approach where all possible paths are explored.
- **Output:**
  ```
  British Museum Search Best Path: ['S', 'A', 'D', 'G'] with cost 6
  ```

### 2. **Depth-First Search (DFS)**
- **Description:** DFS explores each branch of the graph as deeply as possible before backtracking.
- **Output:**
  ```
  DFS Best Path: ['S', 'A', 'D', 'G'] with cost 6
  ```

### 3. **Breadth-First Search (BFS)**
- **Description:** BFS explores all the nodes at the present depth level before moving on to nodes at the next depth level.
- **Output:**
  ```
  BFS Best Path: ['S', 'A', 'D', 'G'] with cost 6
  ```

### 4. **Hill Climbing**
- **Description:** A greedy algorithm that always expands the node with the lowest heuristic value.
- **Output:**
  ```
  Hill Climbing Best Path: ['S', 'A', 'D', 'G'] with cost 6
  ```

### 5. **Beam Search**
- **Description:** Beam Search keeps track of a limited number of best nodes at each level to reduce memory usage.
- **Output:**
  ```
  Beam Search Best Path: ['S', 'A', 'D', 'G'] with cost 6
  ```

### 6. **Oracle Search**
- **Description:** Hypothetical search with perfect knowledge about the shortest path.
- **Output:**
  ```
  Oracle Search Best Path: ['S', 'A', 'D', 'G'] with cost 6
  ```

### 7. **Branch and Bound (B&B)**
- **Description:** B&B explores all possible paths but prunes paths with a higher cost than the best path found so far.
- **Output:**
  ```
  Branch and Bound Best Path: ['S', 'A', 'D', 'G'] with cost 6
  ```

### 8. **Branch and Bound Greedy**
- **Description:** B&B Greedy uses a heuristic to guide the search while also pruning paths.
- **Output:**
  ```
  Branch and Bound Greedy Best Path: ['S', 'A', 'D', 'G'] with cost 6
  ```

### 9. **Branch and Bound Greedy with Exit**
- **Description:** This variation of B&B Greedy exits immediately when the goal node is found.
- **Output:**
  ```
  Branch and Bound Greedy + Exit Best Path: ['S', 'A', 'D', 'G'] with cost 6
  ```

### 10. **Branch and Bound Greedy + Heuristic**
- **Description:** Combines both cost and heuristic aggressively to prune the search space.
- **Output:**
  ```
  Branch and Bound Greedy + Heuristic Best Path: ['S', 'A', 'D', 'G'] with cost 6
  ```

### 11. **Branch and Bound with Heuristic**
- **Description:** Combines the B&B approach with heuristics, exploring nodes based on both cost and heuristic.
- **Output:**
  ```
  Branch and Bound + Heuristic Best Path: ['S', 'A', 'D', 'G'] with cost 6
  ```

### 12. **A* Algorithm**
- **Description:** A* is an informed search algorithm that uses both path cost and heuristics to find the optimal path.
- **Output:**
  ```
  A* Best Path: ['S', 'A', 'D', 'G'] with cost 6
  ```

# Alpha-Beta Pruning in Python

## Description
Alpha-Beta pruning is an optimization technique for the minimax algorithm used in decision-making problems such as game trees. The algorithm efficiently reduces the number of nodes evaluated in the search tree by pruning branches that do not affect the final decision, making the search process faster without sacrificing accuracy.

In the **Minimax Algorithm**, two players alternate between maximizing and minimizing the value of nodes. Alpha-Beta pruning eliminates unnecessary branches in the game tree, avoiding the evaluation of suboptimal moves.

## How it Works
- **Alpha**: The best value that the maximizer (Maximizing player) can guarantee at the current level or higher.
- **Beta**: The best value that the minimizer (Minimizing player) can guarantee at the current level or lower.
- **Pruning**: When alpha is greater than or equal to beta, it implies that no further exploration is needed for the remaining branches of the current node.

In the minimax tree:
1. At each **Maximizing** node, the algorithm tries to maximize the current node’s value, updating `alpha`.
2. At each **Minimizing** node, it tries to minimize the current node’s value, updating `beta`.
3. If at any node, `alpha >= beta`, the branch is pruned (no need to evaluate that branch).

## Example Tree

Consider the following tree:

```
          N1
        /    \
      N2      N3
     /  \    /  \
   N4   N5  N6   N7
  / \   / \  / \  / \
 1   4 7   2 3   0 6   5
```

### Terminal Values (Leaf Nodes): 
`[1, 4, 7, 2, 3, 0, 6, 5]`

- The root `N1` is a **Maximizer**.
- Nodes `N2` and `N3` are **Minimizers**.
- Nodes `N4`, `N5`, `N6`, and `N7` are **Maximizers**.

The algorithm recursively evaluates each node starting from the leaves, alternating between maximizing and minimizing the node values until it reaches the root. The Alpha-Beta pruning mechanism eliminates unnecessary branches to speed up the evaluation.

### Output:
```
The optimal value is: 5
```

