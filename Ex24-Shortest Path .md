## Ex24 — Shortest Path & Reachability in Heritage Town using BFS

## AIM:
To implement a Java program that finds

The shortest number of paths (minimum hops) between two attractions

Total reachable attractions using BFS

## Algorithm

Represent the town map using adjacency lists.

Use BFS to compute:

Minimum hops using distance array

Reachability using visited nodes

Print the results.

## Program
```
Program to find Shortest Path and Reachability in a Heritage Town using BFS.
Developed by: Naresh P.S.
RegisterNumber: 212223040127
Date: 15-11-2025


import java.util.*;

public class HeritageTownBFS {

    public static void main(String[] args) {
        int n = 6;
        List<List<Integer>> graph = new ArrayList<>();
        for (int i = 0; i < n; i++) graph.add(new ArrayList<>());

        graph.get(0).add(1);
        graph.get(0).add(2);
        graph.get(1).add(3);
        graph.get(2).add(4);
        graph.get(4).add(5);

        int start = 0, target = 5;
        int dist[] = new int[n];
        Arrays.fill(dist, -1);

        Queue<Integer> q = new LinkedList<>();
        q.add(start);
        dist[start] = 0;

        while (!q.isEmpty()) {
            int curr = q.poll();
            for (int next : graph.get(curr)) {
                if (dist[next] == -1) {
                    dist[next] = dist[curr] + 1;
                    q.add(next);
                }
            }
        }

        System.out.println("Minimum hops from " + start + " to " + target + ": " + dist[target]);

        int reachable = 0;
        for (int d : dist) if (d != -1) reachable++;

        System.out.println("Total reachable attractions: " + reachable);
    }
}
```

## Output
Minimum hops from 0 to 5: 3
Total reachable attractions: 6

## Result

The program correctly computes the shortest path (minimum hops) and the number of reachable attractions using BFS.
