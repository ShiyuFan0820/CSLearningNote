# Dijkstra

Dijkstra is an algorithm which commonly used to find the shortest path in a graph, it is a single source shortest path algorithm for graphs with non-negative edge weights. 

Single source means at the beginning of the algorithm, a single starting node in a graph should be specified, when execute the algorithm, Dijkstra can find the shortest path between that starting node and all other nodes in the graph.

## Graph

A graph is a data structure that consists of a set of vertices (also called nodes) and a set of edges that connect pairs of vertices. A weighted graph is a graph has weighted edges meaning each edge has a numerical weight or cost associated with it, and can represent the distance between two vertices.

<div align=center>
<img width="350" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/736eec7c-77d7-4942-8872-c7cc11bd16c7">
</div>

## How Dijkstra Work in a Graph

Take this graph as a simple example of how dijkstra works to find the shortest path, in this graph vertex `A` is the starting node:

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/b72686a6-fb5b-459c-b389-cd85a539173d">
</div>

Step 1: Dijkstra algorithm will generate a information which includes all vertex and their shortest distance from the starting vertex, its `A` in this graph, and their previous vertex. When a vertex has not been visited yet, its distance from `A` is positive infinity.

<div align=center>
<img width="400" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/77ba27a8-b9e0-4cb7-a1fb-d0f084aec2f3">
</div>





## Code Implementation
