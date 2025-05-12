# Ex30 Finding Total Cost of Spanning Tree
## DATE: 07/05/2025
## AIM:
To write a C Program to implement Prim's Algorithm for finding Total Cost of spanning tree.
## Algorithm
1. Create a graph representation (using an adjacency matrix or list).
2. Initialize the minimum cost of the spanning tree with the first vertex.
3. Use a priority queue or simple array to select the minimum weight edge that does not form a cycle.
4. Add the edge to the MST and continue until all vertices are included.
5. Output the total cost of the spanning tree.



## Program:
```
/*
Program to implement Prim's Algorithm for finding Total Cost of Spanning Tree
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <limits.h>

#define MAX_VERTICES 10

int graph[MAX_VERTICES][MAX_VERTICES], n;
int parent[MAX_VERTICES], key[MAX_VERTICES], visited[MAX_VERTICES];

int minKey() {
    int min = INT_MAX, min_index;
    for (int v = 0; v < n; v++) {
        if (!visited[v] && key[v] < min) {
            min = key[v];
            min_index = v;
        }
    }
    return min_index;
}

void primMST() {
    for (int i = 0; i < n; i++) {
        key[i] = INT_MAX;
        visited[i] = 0;
    }
    
    key[0] = 0;  // Start from the first vertex
    parent[0] = -1;  // First node has no parent

    for (int count = 0; count < n - 1; count++) {
        int u = minKey();
        visited[u] = 1;

        for (int v = 0; v < n; v++) {
            if (graph[u][v] && !visited[v] && graph[u][v] < key[v]) {
                key[v] = graph[u][v];
                parent[v] = u;
            }
        }
    }
}

int main() {
    printf("Enter the number of vertices: ");
    scanf("%d", &n);

    printf("Enter the adjacency matrix (enter 0 if no edge exists):\n");
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            scanf("%d", &graph[i][j]);
        }
    }

    primMST();

    printf("Edges in the Minimum Spanning Tree (MST):\n");
    int totalCost = 0;
    for (int i = 1; i < n; i++) {
        printf("%d - %d : %d\n", parent[i], i, graph[i][parent[i]]);
        totalCost += graph[i][parent[i]];
    }

    printf("Total cost of the Minimum Spanning Tree is: %d\n", totalCost);
    
    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/5de9e369-7f26-4257-8d16-57f31670143b)



## Result:
Thus the C program to implement Prim's Algorithm for finding Total Cost of spanning tree is implemented successfully.
