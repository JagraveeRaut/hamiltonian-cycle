#include <stdio.h>
 #define MAX 20
 int graph[MAX][MAX];
 int path[MAX];
 int n;
 int isSafe(int v, int pos) {
    if (graph[path[pos - 1]][v] == 0)
        return 0; // Not connected
    for (int i = 0; i < pos; i++)
        if (path[i] == v)
            return 0; // Already visited
    return 1;
 }
 int hamCycleUtil(int pos) {
    if (pos == n) {
        return graph[path[pos - 1]][path[0]] 
== 1; // Check cycle
    }
    for (int v = 1; v < n; v++) {
        if (isSafe(v, pos)) {
            path[pos] = v;
            if (hamCycleUtil(pos + 1))
                return 1;
            path[pos] = -1;
        }
    }
    return 0;
 }
 void hamCycle() {
    for (int i = 0; i < n; i++)
        path[i] = -1;
    path[0] = 0;
    if (hamCycleUtil(1)) {
        printf("Hamiltonian Cycle: ");
        for (int i = 0; i < n; i++)
            printf("%d ", path[i]);
        printf("%d\n", path[0]); // Return to
 start
    } else
        printf("No Hamiltonian Cycle 
exists.\n");
 }
 int main() {
    printf("Enter number of vertices: ");
    scanf("%d", &n);
printf("Enter adjacency matrix 
(%dx%d):\n", n, n);
 for (int i = 0; i < n; i++)
 for (int j = 0; j < n; j++)
 scanf("%d", &graph[i][j]);
 hamCycle();
 return 0;                   }
