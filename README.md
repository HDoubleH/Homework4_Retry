# HDoubleH's Graphs Algorithm Library

This package implements two graph algorithms in python, including **Dijkstra's Shortest Path Algorithm** and **Tarjan's Algorithm for Strongly Connected Components**.

Graphs are data structures which connect nodes identified by labels. 

- **Dijkstra's Shortest Path Algorithm**: This computes the shortest path from a single source node to all the other nodes in a graph. It will find the shortest path from a single source node to all other nodes in a weighted graph with non-negative edge weights. It operates by iteratively expanding the node with the smallest known distance and updating the distances to its neighbors.

- **Tarjan's Algorithm for Strongly Connected Components**: This algorithm detects all the strongly connected components (SCCs) in a directed graph using a depth-first search. A strongly connected component is one which has a path from each vertex to its own, where a strongly connect graph is one where there is a path from each vertex to another vertex. Each SCC is a maximal subgraph where every node is reachable from every other node in the same subgraph. 

## Usage

**Dijkstra's Shortest Path Algorithm**- 
Create a file with the following named filename.py
````
```
from graphs_HDoubleH2 import sp
import sys

if __name__ == '__main__':
    
    if len(sys.argv) != 2:
        print(f'Use: {sys.argv[0]} graph_file')
        sys.exit(1)

    graph = {}
    with open(sys.argv[1], 'rt') as f:
        f.readline() # skip first line
        for line in f:
            line = line.strip()
            s, d, w = line.split()
            s = int(s)
            d = int(d)
            w = int(w)
            if s not in graph:
                graph[s] = {}
            graph[s][d] = w
    
    s = 0
    dist, path = sp.dijkstra(graph, s)
    print(f'Shortest distances from {s}:')
    print(dist)
    for d in path: 
        print(f'spf to {d}: {path[d]}')
```
````

To run this enter the following in the terminal

```
python filename graph.txt

```
**Tarjan's Algorithm for Strongly Connected Components**- 

Create a file with the following named tarjan_filename.py 

````
```

import sys
from graphs_HDoubleH2 import tarjan  # Import Tarjan's Algorithm

if __name__ == '__main__':
    
    if len(sys.argv) != 2:
        print(f'Use: {sys.argv[0]} graph_file')
        sys.exit(1)

    # Load graph from the file
    graph = {}
    with open(sys.argv[1], 'rt') as f:
        f.readline()  # skip the first line
        for line in f:
            line = line.strip()
            s, d, w = line.split()
            s = int(s)
            d = int(d)
            w = int(w)
            if s not in graph:
                graph[s] = {}
            graph[s][d] = w

    # Run Tarjan's Algorithm to find SCCs
    sccs = tarjan.tarjan_scc(graph)
    
    # Output the results
    print(f'Strongly Connected Components (SCCs): {sccs}')

```
````

To run this enter the following in the terminal

```

python tarjan_filename.py graph.txt

```

### Installation 
Package can be installed with:
```
pip3 install graphs_HDoubleH2

```
