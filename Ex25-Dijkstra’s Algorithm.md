## Ex25 — Fastest Route to Charging Station (Dijkstra’s Algorithm)

## AIM:
To design a Java program that finds the shortest travel time from an EV’s current block to the nearest charging station using Dijkstra’s algorithm.

## Algorithm

Represent the town map as a weighted graph.

Use a priority queue (min-heap) for Dijkstra.

Initialize distances to infinity, except source = 0.

Relax edges and update shortest times.

Print shortest time to target charging station.

## Program
```
Program to find the fastest route to a charging station using Dijkstra’s Algorithm.
Developed by: Naresh P.S.
RegisterNumber: 212223040127
Date: 15-11-2025


import java.util.*;

public class DijkstraChargingStation {

    static class Edge {
        int v, w;
        Edge(int v, int w) { this.v = v; this.w = w; }
    }

    public static void main(String[] args) {
        int n = 5;
        List<List<Edge>> graph = new ArrayList<>();

        for (int i = 0; i < n; i++) graph.add(new ArrayList<>());

        graph.get(0).add(new Edge(1, 4));
        graph.get(0).add(new Edge(2, 1));
        graph.get(2).add(new Edge(1, 2));
        graph.get(1).add(new Edge(3, 1));
        graph.get(2).add(new Edge(3, 5));
        graph.get(3).add(new Edge(4, 3));  // Charging Station

        int start = 0;
        int chargingStation = 4;

        int dist[] = new int[n];
        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[start] = 0;

        PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> a[1] - b[1]);
        pq.add(new int[]{start, 0});

        while (!pq.isEmpty()) {
            int curr[] = pq.poll();
            int u = curr[0];

            for (Edge e : graph.get(u)) {
                if (dist[u] + e.w < dist[e.v]) {
                    dist[e.v] = dist[u] + e.w;
                    pq.add(new int[]{e.v, dist[e.v]});
                }
            }
        }

        System.out.println("Fastest travel time to charging station: " + dist[chargingStation]);
    }
}
```

## Output
Fastest travel time to charging station: 8

## Result

The program successfully computes the fastest travel time to the charging station using Dijkstra’s algorithm.
