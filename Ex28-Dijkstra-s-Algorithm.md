# Ex28 Dijkstra’s Algorithm
## DATE: 06/05/2025
## AIM:
To write a C Program to implement Dijkstra's Algorithm to find the shortest path

## Algorithm
1. Initialize the distance to all vertices as infinity and distance to the source as 0.
2. Mark all vertices as unvisited.
3. Select the unvisited vertex with the smallest distance.
4. For the selected vertex, update the distance of its adjacent vertices.
5. Mark the selected vertex as visited.
6. Repeat steps 3–5 until all vertices are visited.



## Program:
```
/*
Program to implement Dijkstra's Algorithm 
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#define INF 9999
#define MAX 10

void dijkstra(int graph[MAX][MAX], int n, int start) {
    int distance[MAX], visited[MAX], count, minDist, nextNode, i, j;

    for (i = 0; i < n; i++) {
        distance[i] = graph[start][i];
        visited[i] = 0;
    }

    distance[start] = 0;
    visited[start] = 1;
    count = 1;

    while (count < n - 1) {
        minDist = INF;

        for (i = 0; i < n; i++) {
            if (distance[i] < minDist && !visited[i]) {
                minDist = distance[i];
                nextNode = i;
            }
        }

        visited[nextNode] = 1;

        for (i = 0; i < n; i++) {
            if (!visited[i]) {
                if (minDist + graph[nextNode][i] < distance[i])
                    distance[i] = minDist + graph[nextNode][i];
            }
        }
        count++;
    }

    printf("Vertex\tDistance from Source %d\n", start);
    for (i = 0; i < n; i++) {
        printf("%d\t%d\n", i, distance[i]);
    }
}

int main() {
    int graph[MAX][MAX], i, j, n, start;

    printf("Enter the number of vertices: ");
    scanf("%d", &n);

    printf("Enter the adjacency matrix (use 9999 for no direct path):\n");
    for (i = 0; i < n; i++)
        for (j = 0; j < n; j++)
            scanf("%d", &graph[i][j]);

    printf("Enter the starting vertex: ");
    scanf("%d", &start);

    dijkstra(graph, n, start);

    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/2456a1c0-f208-40ef-be16-6886fe89edab)



## Result:
Thus, the Program to implement Dijkstra's Algorithm to find the shortest path is implemented successfully.
