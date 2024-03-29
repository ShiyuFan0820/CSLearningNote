# Dijkstra

Dijkstra is an algorithm which commonly used to find the shortest path in a graph, it is a single source shortest path algorithm for graphs with non-negative edge weights. 

Single source means at the beginning of the algorithm, a single starting node in a graph should be specified, when execute the algorithm, Dijkstra can find the shortest path between that starting vertex and all other vertices in the graph.

## Graph

A graph is a data structure that consists of a set of vertices (also called nodes) and a set of edges that connect pairs of vertices. A weighted graph is a graph has weighted edges meaning each edge has a numerical weight or cost associated with it, and can represent the distance between two vertices.

<div align=center>
<img width="350" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/736eec7c-77d7-4942-8872-c7cc11bd16c7">
</div>

## How Dijkstra Works in a Graph

Take this graph as a simple example of how dijkstra works to find the shortest path, in this graph vertex `A` is the starting node (This graph construction doesn't conform to the triangle formation principle, but never mind, it just as an example to show how Dijkstra works):

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/b72686a6-fb5b-459c-b389-cd85a539173d">
</div>

Step 1: Dijkstra algorithm will generate a information which includes all vertices and their shortest distance from the starting vertex, its `A` in this graph, and their previous vertices. When a vertex has not been visited yet, its distance from `A` is assumed as positive infinity.

<div align=center>
<img width="400" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/77ba27a8-b9e0-4cb7-a1fb-d0f084aec2f3">
</div>

Step 2: Start from `A`, check vertices which connect with `A`, in this graph, they are `B` and `D`, compare their distance from `A` with their current distance from `A` which is `+∞`, replace with smaller values, and record their previous vertex.
<div align=center>
<img width="400" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/c6d7da73-96d7-43bb-be73-809182b42ecb">
</div>

Step 3: Always visit the vertex which is closer to `A`, so visit `D` first, `D` is connected with `A`, `B`, and `E`, path `A` and `E` is already visited, so look at `B`. The distance between `D` and `B` is `2`, so the distance `B` through `D` to `A` is 3, compare with the original distance `7`, new distance is closer, so modify `B`'s information. Repeat the same step with `E`.
<div align=center>
<img width="400" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/c8e37e96-2ca4-40f2-8f61-161a0fc3cb3b">
</div>

Step 4: Now `E` has the closest distance from `A`, so visit `E` first, repeat the same step as visit `D`, the updated information is as below.
<div align=center>
<img width="400" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/c2c2f5e0-525b-4888-9895-261a3dc37a89">
</div>

Step 5: Then visit `B` and `C`, repeat the step and update the information, then the shortest path between starting vertex `A` and all other vertices in the graph is found. For example, if we want to know from `A` to `C`, which path is the shortest, we can check vertex `C`, the shortest distance from `A` is `7`, and its previous vertex is `E`, the previous vertex of `E` is `D`, and the previous vertex of `D` is `A`, so the shortest path and distance from `A` to `C` is found, its `A` to `D` to `E` to `C` with the distance of `7`.
<div align=center>
<img width="400" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/7adc0320-8e13-4ebf-b110-3b18a0caab52">
</div>

## Code Implementation

The above example is shown in code:
```py
graph = {
    "A": {"B": 7, "D": 1},
    "B": {"A": 7, "D": 2, "E": 2, "C": 5},
    "C": {"B": 5, "E": 5},
    "D": {"A": 1, "B": 2, "E": 1},
    "E": {"D": 1, "B": 2, "C": 5}
}
# Determine a starting vertex and a destination.
from_vert = "A"
to_vert = "C"
# Define a visited list to store all the visited vertices
visited = []
# Define a dictionary to record all shortest paths or distances from start vertex to all other vertices.
shortest_paths = {}
# Define another dictionary to record distances during the process and add the shortest path in the shortest path dictionary.
dis_from_start = {}
# Add starting vertex A to the dis_from_start dictionary first, make the distance from A be the key, and vertex name and its previous vertex as key value pair be the value of the distance key.
## The reason why I make the distance from A be the key is that meybe there are more than one vertex whose distance from A is the same, so if there is another vertex whose distance from A is the same with another one, the new vertex name and its previous vertex as key value pair can be append to the distance key's value list.
dis_from_start[0] = [{"vert": from_vert, "pre": "-"}]

while dis_from_start:
    # Always visit the vertex which has the shortest distance from A, so the distance key with the minimal value will be visited first, here actually use the concept of priority queue.
    closest_dis = min(dis_from_start.keys())
    # If there is more than one vertex of this distance, visit the first one first.
    closest_pair = dis_from_start[closest_dis].pop(0)
    # If all vertices of this distance has been visited, delete the distance key in the dictionary.
    if not dis_from_start[closest_dis]:
        del dis_from_start[closest_dis]
    visit_vert = closest_pair["vert"]
    # When we visit a vertex if it's not in the shortest_paths, add it's current shortest distance from A and it's previous vertex.
    if visit_vert not in shortest_paths:
        shortest_paths[visit_vert] = {"dis": closest_dis, "pre": closest_pair["pre"]}
        # Check if the visit_vert is equal to the to_vert, if not, continue searching the neighbours.
        if visit_vert == to_vert:
            break
        # Search for its neighbours.
        neighbour_verts = graph[visit_vert]
        for vert, dis in neighbour_verts.items():
            if vert not in visited:
                new_dis = dis + closest_dis
                if new_dis not in dis_from_start:
                    dis_from_start[new_dis] = []
                dis_from_start[new_dis].append({"vert": vert, "pre": visit_vert})
    # If this vertex is alreay visited, but its new distance is shorter than the last one, the new distance and previous vertex would replace the old one.
    elif shortest_paths[visit_vert]["dis"] > closest_dis:
        shortest_paths[visit_vert] = {"dis": closest_dis, "pre": closest_pair["pre"]}
    visited.append(visit_vert)
print(shortest_paths)

print(f"Shortest path found from {from_vert} to {to_vert}:")
# Back tracking the path.
path = [to_vert]
while shortest_paths[to_vert]["pre"] != from_vert:
    path.append(shortest_paths[to_vert]["pre"])
    to_vert = shortest_paths[to_vert]["pre"]
path.append(from_vert)
path.reverse()
print("-->".join(path))

```

The output is:
```py
{'A': {'dis': 0, 'pre': '-'}, 'D': {'dis': 1, 'pre': 'A'}, 'E': {'dis': 2, 'pre': 'D'}, 'B': {'dis': 3, 'pre': 'D'}, 'C': {'dis': 7, 'pre': 'E'}}
Shortest path found from A to C:
A-->D-->E-->C
```

I also tested the situation when I changed the `to_vert` to other vertex, this code still works.

## Time Complexity of Dijkstra's Algorithm

The time complexity of Dijkstra's algorithm is `O((V + E)logV)`, `V` is the number of vertex in the graph, `E` is the number of edges in the graph. 

In Dijkstra's algorithm, the priority queue is used to select the vertex with the minimum distance to the source/start vertex. This operation is performed for each vertex in the graph, in the worst case, each edge and vertex may be visited once during the execution, so the time complexity is `O(V)`, and priority queue operates insertions and extractions, the relaxing edges is `O(E)`, so its typically `O(V + E)`, As there is a priority queue to extract the minimal distance from the starting vertex, the time complexity of the priority queue is `O(logV)` (This is because priority queues are commonly implemented by binary heaps like binary tree), so the time complexity of Dijkstra's algorithm is `O((V + E)logV)`.





