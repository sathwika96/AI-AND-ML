# AI-AND-ML<br>
# 1.BREADTH FIRST SEARCH<br>
graph={<br>
    '1':['2','10'],<br>
    '2':['3','8'],<br>
    '3':['4'],<br>
    '4':['5','6','7'],<br>
    '5':[],<br>
    '6':[],<br>
    '7':[],<br>
    '8':['9'],<br>
    '9':[],<br>
    '10':[]<br>
}<br>
visited=[]<br>
queue=[]<br>
def bfs(visited,graph,node):<br>
    visited.append(node)<br>
    queue.append(node)<br>
    while queue:<br>
        m=queue.pop(0)<br>
        print(m,end=' ')<br>
        for neighbour in graph[m]:<br>
            if neighbour not in visited:<br>
                visited.append(neighbour)<br>
                queue.append(neighbour)<br>
print("Following is the Breadth-First Search")<br>
bfs(visited,graph,'1')<br>
# OUTPUT:-<br>
![image](https://user-images.githubusercontent.com/119857004/207017267-ef7f17f9-2e17-4e6e-b089-a513297d83ab.png)<br>
# 2. DEPTH FIRST SEARCH<br>
graph={<br>
    '5':['3','7'],<br>
    '3':['2','4'],<br>
    '7':['6'],<br>
    '6':[],<br>
    '2':['1'],<br>
    '1':[],<br>
    '4':['8'],<br>
    '8':[]   <br> 
}<br>
visited=set()<br>
def dfs(visited,graph,node):<br>
    if node not in visited:<br>
        print(node)<br>
        visited.add(node)<br>
        for neighbour in graph[node]:<br>
            dfs(visited,graph,neighbour)<br>
print("Following is the Depth-First Search")<br>
dfs(visited,graph,'5')<br>
# OUTPUT:-
![image](https://user-images.githubusercontent.com/119857004/207017930-64eafcc6-ff24-4860-992d-523f92e8632e.png)<b>
# 3.BEST FIRST SEARCH<br>
from queue import PriorityQueue <br>
import matplotlib.pyplot as plt <br>
import networkx as nx <br>
for implementing BFS | returns path having lowest cost<br>
def best_first_search(source, target, n): <br>
    visited = [0] * n <br>
    visited[source] = True <br>
    pq = PriorityQueue() <br>
    pq.put((0, source)) <br>
    while pq.empty() == False: <br>
        u = pq.get()[1] <br>
        print(u, end=" ") # the path having lowest cost <br>
        if u == target: <br>
            break <br>
        for v, c in graph[u]: <br>
                if visited[v] == False: <br>
                    visited[v] = True <br>
                    pq.put((c, v)) <br>
                    #print() <br>
for adding edges to graph <br>
def addedge(x, y, cost): <br>
    graph[x].append((y, cost)) <br>
    graph[y].append((x, cost))<br>

v = int(input("Enter the number of nodes: "))<br>
graph = [[] for i in range(v)] # undirected Graph <br>
e = int(input("Enter the number of edges: ")) <br>
print("Enter the edges along with their weights:")<br>
for i in range(e): <br>
    x, y, z = list(map(int, input().split())) <br>
    addedge(x, y, z) <br>
source = int(input("Enter the Source Node: "))<br>
target = int(input("Enter the Target/Destination Node: ")) <br>
print("\nPath: ", end = "") <br>
best_first_search(source, target, v) <br>
![image](https://user-images.githubusercontent.com/119857004/208890992-33082048-655f-4375-a7e3-b628f2019aec.png)<br>
# 4.WATER JUG<br>
    from collections import defaultdict <br>
jug1, jug2, aim = 4, 3, 2 <br>
visited = defaultdict(lambda: False) <br>
def waterJugSolver(amt1, amt2): <br>
    if (amt1 == aim and amt2 == 0) or (amt2 == aim and amt1 == 0):  <br>
        print(amt1, amt2) <br>
        return True <br>
    if visited[(amt1, amt2)] == False: <br>
        print(amt1, amt2) <br>
        visited[(amt1, amt2)] = True <br>
        return (waterJugSolver(0, amt2) or <br>
                waterJugSolver(amt1, 0) or <br>
                waterJugSolver(jug1, amt2) or <br>
                waterJugSolver(amt1, jug2) or <br>
                waterJugSolver(amt1 + min(amt2, (jug1-amt1)), <br>
                               amt2 - min(amt2, (jug1-amt1))) or <br>
                waterJugSolver(amt1 - min(amt1, (jug2-amt2)),<br> 
                               amt2 + min(amt1, (jug2-amt2)))) <br>
    else: <br>
        return False <br>
print("Steps: ") <br>
waterJugSolver(0, 0)<br>
![image](https://user-images.githubusercontent.com/119857004/208891624-47f598c6-de1a-4454-9322-629948291cfe.png)<br>
