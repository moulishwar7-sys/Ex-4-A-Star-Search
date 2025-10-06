<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: MOULISHWAR G     </h3>
<h3>Register Number: 2305001020          </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


// A* Search Algorithm
1. Initialize:
    - q: priority queue with the start node s and its heuristic value h[s]
    - v: set to keep track of visited nodes

2. While q is not empty:
    - Dequeue the node u with the minimum f value (f = g + h)
    - If u is the goal node t, return the path
    - Mark u as visited
    - For each neighbor x of u that has not been visited:
        - Calculate the tentative g value (g_ + c)
        - Calculate the f value (g_ + c + h[x])
        - Enqueue x with its f value

3. If q is empty and no path is found, return "No path found"


## PROGRAM
```python
import heapq

def astar(g, s, t, h):
    q = [(h[s], 0, s, [])]; v = set()
    while q:
        f, g_, u, p = heapq.heappop(q)
        if u == t: return p + [u]
        if u in v: continue
        v.add(u)
        for x, c in g.get(u, []):
            if x not in v:
                heapq.heappush(q, (g_ + c + h.get(x, 0), g_ + c, x, p + [u]))
    return None

g = {}
print("Edges: from to cost (type 'done' to end):")
while (e := input()) != "done":
    u, v, c = e.split(); g.setdefault(u, []).append((v, int(c)))

h = {n: int(input(f"Heuristic for {n}: ")) for n in g}
s = input("Start: "); t = input("Goal: ")
print("Path:", astar(g, s, t, h) or "No path found")


```

## GRAPH 

![277151990-b1377c3f-011a-4c0f-a843-516842ae056a](https://github.com/user-attachments/assets/bedfaca4-a69a-468a-957d-a3def3f28836)


## INPUT
<hr>
A B 2 <br>
A C 3 <br>
B D 1 <br>
B E 4 <br>
C F 2 <br>
D G 1 <br>
E G 3 <br>
F G 2 <br>
done <br>
<hr>

## Output

<img width="968" height="439" alt="Screenshot 2025-10-06 141613" src="https://github.com/user-attachments/assets/55365972-7a69-461c-885c-cb8b48a2c65f" />



## RESULT

Thus, the program successfully finds the shortest path from the start node to the goal node using the A* algorithm.
