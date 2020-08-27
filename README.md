# leetcode 70 - Climbing Stairs


## Approach: Fibonacci Number
```C#
public static int ClimbStairs(int n)
{
    if (n < 3) return n;
    int prev1 = 1,
        prev2 = 2;
    int steps = 1;
    for(int i = 3; i <= n; i++)
    {
        steps = prev1 + prev2;
        prev1 = prev2;
        prev2 = steps;
    }
    return steps;
}
```
#### Complexity Analysis
* Time Complexity: O(n)
* Space Complexity: O(1)

## Approach: Recursion with Memoization
```C#
public static int ClimbStairs(int n)
{
    var cached = new int[n + 1];
    return ClimbDP(n, cached);
}

private static int ClimbDP(int n, int[] cached)
{
    if (n <= 3) return n;
    if (cached[n] != 0) return cached[n];

    cached[n] = ClimbDP(n - 1, cached) + ClimbDP(n - 2, cached);
    return cached[n];
}
```
#### Complexity Analysis
* Time Complexity: O(n)
* Space Complexity: O(n)


## Approach: Fibonacci Formula

Fn = 1/sqrt(5) ( ( ( (1 + sqrt(5)) / 2) ^ n + 1) - ( ( (1 - sqrt(5)) / 2) ^ n + 1)

```C#
public int ClimbStairs(int n)
{
    double sqrt5 = Math.Sqrt(5);
    double fibn = Math.Pow((1 + sqrt5) / 2, n + 1) - Math.Pow((1 - sqrt5) / 2, n + 1);
    return (int)(fibn / sqrt5);
}
```
#### Complexity Analysis
* Time Complexity: O(log n), log n for pow method
* Space Complexity: O(1)
