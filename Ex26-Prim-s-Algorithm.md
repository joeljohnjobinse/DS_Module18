# Ex26 Prim’s Algorithm
## DATE: 06/05/2025
## AIM:
To write a C program to implement Prim's Algorithm for finding Total Cost of tree.

## Algorithm
1. Create a cost matrix of the graph.
2. Initialize arrays for visited nodes, minimum edge costs, and parent nodes.
3. Choose an arbitrary starting node and mark it as visited.
4. For all unvisited nodes, update their minimum edge cost if a smaller edge is found.
5. Repeat until all nodes are included in the MST.
6. Display edges used and calculate total cost.

## Program:
```
/*
Program to implement Prim's Algorithm
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <limits.h>

#define MAX 100
#define INF 9999

int findMinVertex(int cost[], int visited[], int n) {
    int min = INF, minIndex = -1;
    for (int i = 0; i < n; i++) {
        if (!visited[i] && cost[i] < min) {
            min = cost[i];
            minIndex = i;
        }
    }
    return minIndex;
}

void primMST(int graph[MAX][MAX], int n) {
    int parent[MAX], cost[MAX], visited[MAX];
    int totalCost = 0;

    for (int i = 0; i < n; i++) {
        cost[i] = INF;
        visited[i] = 0;
    }

    cost[0] = 0;  // Start from node 0
    parent[0] = -1;

    for (int count = 0; count < n - 1; count++) {
        int u = findMinVertex(cost, visited, n);
        visited[u] = 1;

        for (int v = 0; v < n; v++) {
            if (graph[u][v] && !visited[v] && graph[u][v] < cost[v]) {
                parent[v] = u;
                cost[v] = graph[u][v];
            }
        }
    }

    printf("Edge \tWeight\n");
    for (int i = 1; i < n; i++) {
        printf("%d - %d \t%d \n", parent[i], i, graph[i][parent[i]]);
        totalCost += graph[i][parent[i]];
    }

    printf("Total cost of MST: %d\n", totalCost);
}

int main() {
    int graph[MAX][MAX], n;
    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter the adjacency matrix (use 0 if no edge):\n");
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++) {
            scanf("%d", &graph[i][j]);
            if (graph[i][j] == 0)
                graph[i][j] = INF;
        }

    primMST(graph, n);
    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/e02b95af-671c-40ff-9df2-82c292f7c8f8)



## Result:
Thus, the C program to implement Prim's Algorithm for finding Total Cost of tree is implemented successfully.
