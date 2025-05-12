# Ex27 Kruskal’s Algorithm
## DATE: 06/05/2025
## AIM:
To write a C program to implement Kruskal's Algorithm for finding minimum cost

## Algorithm
1. Sort all edges in non-decreasing order of their weights.
2. Pick the smallest edge. Check if it forms a cycle using Union-Find.
3. If it doesn't form a cycle, include it in the MST.
4. Repeat until the MST contains (V-1) edges.
5. Output the selected edges and total cost.

## Program:
```
/*
Program to implement Kruskal's Algorithm
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

typedef struct {
    int u, v, weight;
} Edge;

int parent[MAX];

int find(int i) {
    while (parent[i])
        i = parent[i];
    return i;
}

int union_set(int i, int j) {
    if (i != j) {
        parent[j] = i;
        return 1;
    }
    return 0;
}

int compare(const void* a, const void* b) {
    Edge* e1 = (Edge*)a;
    Edge* e2 = (Edge*)b;
    return e1->weight - e2->weight;
}

void kruskal(Edge edges[], int n, int e) {
    int i, j, u, v, total = 0;
    Edge result[MAX];
    int count = 0;

    qsort(edges, e, sizeof(Edge), compare);

    for (i = 0; i < e; i++) {
        u = find(edges[i].u);
        v = find(edges[i].v);
        if (union_set(u, v)) {
            result[count++] = edges[i];
            total += edges[i].weight;
        }
        if (count == n - 1)
            break;
    }

    printf("Edge \tWeight\n");
    for (i = 0; i < count; i++)
        printf("%d - %d \t%d\n", result[i].u, result[i].v, result[i].weight);

    printf("Total cost of MST: %d\n", total);
}

int main() {
    int n, e;
    Edge edges[MAX];

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter number of edges: ");
    scanf("%d", &e);

    printf("Enter %d edges (u v weight):\n", e);
    for (int i = 0; i < e; i++) {
        scanf("%d%d%d", &edges[i].u, &edges[i].v, &edges[i].weight);
    }

    kruskal(edges, n, e);
    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/3106f941-e6ea-4b47-ac2e-4b91e7279b2b)



## Result:
Thus, the C program to implement Kruskal's Algorithm for finding minimum cost is implemented successfully.
