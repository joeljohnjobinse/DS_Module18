# Ex29 Travelling Salesman Problem
## DATE:
## AIM:
To write a C Program to implement Travelling Salesman Problem for finding shortest path.
## Algorithm
1. Use a brute-force approach to check all possible permutations of cities and calculate the total distance for each permutation.
2. Track the minimum distance encountered.
3. Output the minimum path and the distance.



## Program:
```
/*
Program to implement Travelling Salesman Problem for finding shortest path
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <limits.h>

#define MAX_CITIES 10

int dist[MAX_CITIES][MAX_CITIES], n;
int visited[MAX_CITIES];

int tsp(int city, int count, int cost, int start) {
    if (count == n && dist[city][start] != 0) {
        return cost + dist[city][start];
    }

    int ans = INT_MAX;
    for (int nextCity = 0; nextCity < n; nextCity++) {
        if (!visited[nextCity] && dist[city][nextCity] != 0) {
            visited[nextCity] = 1;
            int newCost = tsp(nextCity, count + 1, cost + dist[city][nextCity], start);
            visited[nextCity] = 0;
            ans = (newCost < ans) ? newCost : ans;
        }
    }
    return ans;
}

int main() {
    printf("Enter the number of cities: ");
    scanf("%d", &n);

    printf("Enter the distance matrix (use 0 for no direct path):\n");
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            scanf("%d", &dist[i][j]);
        }
    }

    for (int i = 0; i < n; i++) {
        visited[i] = 0;
    }

    visited[0] = 1;  // Start from city 0
    int minCost = tsp(0, 1, 0, 0); // Call the TSP function

    printf("The minimum cost of visiting all cities is: %d\n", minCost);
    
    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/8dd62932-4426-4a18-b318-b6ff7fbce87b)



## Result:
Thus, the C program to implement Travelling Salesman Problem for finding shortest path is implemented successfully.
