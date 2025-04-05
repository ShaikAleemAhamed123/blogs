---
title: Diameter_of_Undirected_graph.md
draft: false
---
*Solution*: 

1. start at an arbitrary node and find the farthest node from it let’s call it **FN** (use dfs/bfs).
2. Now from **FA** find the farthest node.. this will give you the diameter of the undirected graph

*Why does the above approach work ?*

- In a tree, the diameter is always the longest path between two nodes.
- Starting from any arbitrary node, the farthest node from it will always be one endpoint of the diameter.
- From that endpoint, the farthest node will be the other endpoint of the diameter.

This approach runs in **O(V + E)** time since it involves two traversals of the tree.

--------------------------------------------------------------------------

### tags
#algorithms #graph