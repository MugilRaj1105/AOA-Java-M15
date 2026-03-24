
# EX 5E Minimum Spanning Tree -Boruvka's Algorithm
## AIM:
To write a Java program to for given constraints.
Boruvka's Algorithm - Minimum Spanning Tree

Find the MST using Boruvka's Algorithm for a weighted undirected graph.
<img width="292" height="235" alt="image" src="https://github.com/user-attachments/assets/06246b27-37a9-40a8-bd7a-37a1d5187cd1" />

## Algorithm
1. Read the number of vertices **V** and edges **E**.
2. Initialize each vertex as its own component using **Disjoint Set Union (DSU)**.
3. While more than one component exists:

   * Create an array `cheapest[]` to store the cheapest edge for each component.
   * For each edge, determine the components of its endpoints using DSU:

     * If they belong to different components, update the cheapest edge for those components.
   * For every component, add the cheapest edge to the MST if it does not form a cycle.
   * Union the components connected by these edges and reduce the component count.
4. Continue until only one component remains.
5. Print all selected MST edges and the total weight. 

## Program:
```
/*
Program to implement Reverse a String
Developed by: MUGIL RAJ S A
Register Number: 212223220062
import java.util.*;

public class BoruvkaMST {
    static int[] parent;

    static int find(int i) {
        if (parent[i] != i)
            parent[i] = find(parent[i]);
        return parent[i];
    }

    static void union(int x, int y) {
        parent[find(x)] = find(y);
    }

    
    static int boruvkaMST(int V, List<Edge> edges) {
        //Type your code here
        parent=new int[V];
        for(int i =0;i<V;i++) parent[i]=i;
        int components=V;
        int mstweight=0;
        while(components>1){
            Edge[] cheapest = new Edge[V];
            for(Edge e: edges){
                int set1=find(e.src),set2=find(e.dest);
                if(set1==set2) continue;
                if(cheapest[set1]==null||cheapest[set1].weight>e.weight) cheapest[set1]=e;
                if(cheapest[set2]==null||cheapest[set2].weight>e.weight) cheapest[set2]=e;
            }
            for(int i=0;i<V;i++){
                Edge e =cheapest[i];
                if(e!=null){
                    int s1=find(e.src);
                    int s2=find(e.dest);
                    
                    if(s1!=s2){
                        mstweight+=e.weight;
                        System.out.println("Edge: "+e.src+"-"+e.dest+" Weight: "+e.weight);
                        union(s1,s2);
                        components--;
                    }
                }
            }
        }
        return mstweight;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int V = sc.nextInt();
        int E = sc.nextInt();

        List<Edge> edges = new ArrayList<>();
        for (int i = 0; i < E; i++) {
            edges.add(new Edge(sc.nextInt(), sc.nextInt(), sc.nextInt()));
        }

        int totalWeight = boruvkaMST(V, edges);
        System.out.println("Total Weight of MST: " + totalWeight);

        sc.close();
    }
}

class Edge {
    int src, dest, weight;
    Edge(int s, int d, int w) {
        src = s; dest = d; weight = w;
    }
}

*/
```

## Output:
<img width="636" height="495" alt="image" src="https://github.com/user-attachments/assets/df9f5510-6774-4994-b8ba-f0c69b7c988c" />



## Result:
The program successfully implemented and the expected output is verified.
