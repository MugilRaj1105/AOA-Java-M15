
# EX 5A 0/1 Knapsack Problem - Branch&Bound 
## AIM:
To Write a Java program to solve 0/1 Knapsack problem using Branch and Bound Approach.
You are heading a college entrepreneurship cell that can invest in up to N student‑startups.

For each startup i you know: cost[i]  — the amount (in ₹ lakh) required to join the showcase profit[i] — the estimated profit (in ₹ lakh) you’ll gain if it succeeds You have a total budget of B ₹ lakh. Pick a subset of startups so that the sum of costs ≤ B and the sum of profits is maximised.

Because N can be as large as 50, a plain exhaustive search (2^N) is too slow.

The recommended approach is Branch & Bound with a fractional‑knapsack upper bound (but any algorithm that meets the constraints is accepted). 

Input Format

N

B

cost[1] cost[2] … cost[N]

profit[1] profit[2] … profit[N]

1 ≤ N ≤ 50

1 ≤ B ≤ 1 000 000

1 ≤ cost[i], profit[i] ≤ 10 000 

Output Format

maxProfit

For example:




## Algorithm
1. Read the number of startups **N**, the available budget **B**, and the arrays **cost[]** and **profit[]**.
2. Sort the startups in descending order of **profit-to-cost ratio** to improve bound tightness.
3. Use a **Depth-First Search Branch & Bound** approach:

   * Maintain current cost, current profit, and current index.
4. Compute an **upper bound** for each node using the **fractional knapsack** idea:

   * Add full projects while possible.
   * Add fractional part of the next project to estimate maximum possible profit.
5. If the upper bound ≤ current best profit → **prune** the branch.
6. Recursively explore:

   * Including the current project (if cost ≤ B)
   * Excluding the current project
7. Keep track of the **best maximum profit** found.
8. Print the maximum achievable profit.
## Program:
```
/*
Program to implement Reverse a String
Developed by: MUGIL RAJ S A
Register Number: 212223220062
import java.util.*;

public class StartupShowcaseOptimizer {

    // ---------- Global data ----------
    static int N, B;
    static int[] c, p;          // cost, profit after sorting by ratio
    static int best = 0;        // incumbent best profit

    // ---------- Fractional upper bound ----------
    static double bound(int idx, int cw, int cv) {
        double b = cv;
        int w = cw;

        // Take items fractionally until budget exceeded
        for (int i = idx; i < N; i++) {
            if (w + c[i] <= B) {
                w += c[i];
                b += p[i];
            } else {
                // Take fractionally
                b += (double)(B - w) / c[i] * p[i];
                break;
            }
        }
        return b;
    }

    // ---------- DFS Branch & Bound ----------
    static void dfs(int idx, int cw, int cv) {
        if (cw > B) return;             // Exceeds budget → prune
        if (cv > best) best = cv;       // Update best profit
        if (idx >= N) return;           // No more items

        // Bound check: can we improve over current best?
        if (bound(idx, cw, cv) <= best) return;  // Prune

        // Take the current item
        dfs(idx + 1, cw + c[idx], cv + p[idx]);

        // Skip the current item
        dfs(idx + 1, cw, cv);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        N = sc.nextInt();
        B = sc.nextInt();
        int[] cost = new int[N];
        int[] prof = new int[N];
        for (int i = 0; i < N; i++) cost[i] = sc.nextInt();
        for (int i = 0; i < N; i++) prof[i] = sc.nextInt();
        sc.close();

        // Sort by profit/cost ratio descending → tighter bounds
        Integer[] idx = new Integer[N];
        Arrays.setAll(idx, i -> i);
        Arrays.sort(idx, Comparator.comparingDouble(i -> -(double) prof[i] / cost[i]));

        c = new int[N];
        p = new int[N];
        for (int i = 0; i < N; i++) {
            c[i] = cost[idx[i]];
            p[i] = prof[idx[i]];
        }

        dfs(0, 0, 0);
        System.out.println(best);
    }
}
*/
```

## Output:
<img width="361" height="235" alt="image" src="https://github.com/user-attachments/assets/6a203239-08c5-4931-8acf-781a07e2ab09" />



## Result:
The program successfully solved 0/1 Knapsack problem using branch & bound and output is verified. 
