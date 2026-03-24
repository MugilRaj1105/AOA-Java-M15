
# EX 5D Flower Planting.
## AIM:
To write a Java program to for given constraints.
You are given n gardens, labelled from 1 to n.

You also have a list called paths, where each element paths[i] = [xi, yi] represents a bidirectional road connectingthe  garden xi and garden yi.

You want to plant one flower in each garden, and there are exactly 4 types of flowers labelled as 1, 2, 3, and 4.

Your goal is to plant flowers such that:

No two connected gardens (i.e., connected via a path) have the same flower type.

Return any valid flower assignment as an array where:

answer[i] is the flower type planted in the (i+1) ᵗʰ garden

It is guaranteed that:

No garden is connected to more than 3 other gardens

A valid flower assignment always exists

<img width="177" height="292" alt="image" src="https://github.com/user-attachments/assets/36aa40cb-1cdd-4746-b1a6-fc51ce6e96aa" />

## Algorithm
1. Read the number of gardens **n** and number of paths **m**.
2. Build an adjacency list to represent the bidirectional paths between gardens.
3. Create an array `res[]` of size `n` to store the assigned flower types.
4. For each garden:

   * Check all its neighbours and mark the flower types used by those neighbours.
   * Assign the **smallest flower type (1 to 4)** that is not used by its neighbours.
5. Print the resulting flower assignment.
6. Since each garden has at most 3 neighbours, at least one of the four flower types will always be available.  

## Program:
```
/*
Program to implement Reverse a String
Developed by: MUGIL RAJ S A
Register Number:  212223220062
import java.util.*;

public class GardenFlowerPlanner {

    public static int[] assignFlowers(int n, int[][] paths) {
        @SuppressWarnings("unchecked")
        List<Integer>[] adj = new ArrayList[n];
        // Type Your Code Here.
        for(int i=0;i<n;i++){
            adj[i]=new ArrayList<>();
        }
        for(int[] path:paths){
           int a = path[0] - 1;
           int b = path[1] - 1; 
           adj[a].add(b); 
           adj[b].add(a);
        }
        int[] result = new int[n];
        
        for(int i=0;i<n;i++){
            boolean[] visit = new boolean[5];
            
            for(int ne: adj[i]){
                int a = result[ne];
                if(a!=0){
                    visit[a]=true;
                }
            }
            for(int i1=1;i1<=4;i1++){
                if(!visit[i1]){
                    result[i]=i1;
                    break;
                }
            }
        }
        return result;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt(); 
        int m = sc.nextInt(); 

        int[][] paths = new int[m][2];
        for (int i = 0; i < m; i++) {
            paths[i][0] = sc.nextInt();
            paths[i][1] = sc.nextInt();
        }
        int[] result = assignFlowers(n, paths);

        for (int flower : result) {
            System.out.print(flower + " ");
        }
        System.out.println();
    }
}

*/
```

## Output:
<img width="386" height="471" alt="image" src="https://github.com/user-attachments/assets/289de0ab-c004-41e1-afbd-c89c4eae3489" />



## Result:
The program successfully implemented and the expected output is verified.
