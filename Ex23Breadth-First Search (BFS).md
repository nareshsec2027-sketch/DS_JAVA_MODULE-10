## Ex23 — BFS Traversal of a City Junction Map

## AIM:
To implement BFS traversal on a city junction map and find all reachable locations from a given source node.

## Algorithm

Represent the city map using an adjacency list.

Maintain a visited array.

Use a queue for BFS traversal.

Start from the source junction and visit all reachable nodes.

Print them in BFS order.

## Program
```
Program to perform BFS traversal on a city's junction map.
Developed by: Naresh P.S.
RegisterNumber: 212223040127
Date: 15-11-2025


import java.util.*;

public class CityBFS {

    public static void main(String[] args) {
        int nodes = 5;
        List<List<Integer>> graph = new ArrayList<>();

        for (int i = 0; i < nodes; i++) graph.add(new ArrayList<>());

        graph.get(0).add(1);
        graph.get(0).add(2);
        graph.get(1).add(3);
        graph.get(2).add(4);

        boolean visited[] = new boolean[nodes];
        Queue<Integer> q = new LinkedList<>();

        int start = 0;
        visited[start] = true;
        q.add(start);

        System.out.print("Reachable locations: ");

        while (!q.isEmpty()) {
            int curr = q.poll();
            System.out.print(curr + " ");

            for (int next : graph.get(curr)) {
                if (!visited[next]) {
                    visited[next] = true;
                    q.add(next);
                }
            }
        }
    }
}
```

## Output
Reachable locations: 0 1 2 3 4

## Result

The program successfully performs BFS traversal on a city-junction map and lists all reachable locations from the source.
