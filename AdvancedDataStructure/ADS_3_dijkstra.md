# Dijkstra

Dijkstra is an algorithm which commonly used to find the shortest path in a graph, it is a single source shortest path algorithm for graphs with non-negative edge weights. 

Single source means at the beginning of the algorithm, a single starting node in a graph should be specified, when execute the algorithm, Dijkstra can find the shortest path between that starting vertex and all other vertices in the graph.

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

Step 1: Dijkstra algorithm will generate a information which includes all vertices and their shortest distance from the starting vertex, its `A` in this graph, and their previous vertices. When a vertex has not been visited yet, its distance from `A` is positive infinity.

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

## Code Implementation (need to be modified)

The above example is shown in code:
```py
graph = {
    "A": {"B": 7, "D": 1},
    "B": {"A": 7, "D": 2, "E": 2, "C": 5},
    "C": {"B": 5, "E": 5},
    "D": {"A": 1, "B": 2, "E": 1},
    "E": {"D": 1, "B": 2, "C": 5}
}
visited = {}
dis_from_start = {}
dis_from_start[0] = [{"vert": "A", "pre": "-"}]
print(dis_from_start)
while dis_from_start:
    closest_dis = min(dis_from_start.keys())
    closest_vert = dis_from_start[closest_dis].pop(0)
    print(closest_vert)
    if not dis_from_start[closest_dis]:
        del dis_from_start[closest_dis]
    visit_vert = closest_vert["vert"]
    print(visit_vert)
    if visit_vert not in visited:
        visited[visit_vert] = {"dis": closest_dis, "pre": closest_vert["pre"]}
        print(visited)
        neighbour_verts = graph[visit_vert]
        print(neighbour_verts)
        for vert, dis in neighbour_verts.items():
            if dis not in dis_from_start:
                dis_from_start[dis] = []
            dis_from_start[dis].append({"vert": vert, "pre": visit_vert})
    elif visited[visit_vert]["dis"] > closest_dis:
        visited[visit_vert] = {"dis": closest_dis, "pre": closest_vert["pre"]}
print(visited)
```
