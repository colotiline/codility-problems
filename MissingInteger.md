# Problem
Write a function:

class Solution { public int solution(int[] A); }

that, given an array A of N integers, returns the smallest positive integer (greater than 0) that does not occur in A.

For example, given A = [1, 3, 6, 4, 1, 2], the function should return 5.

Given A = [1, 2, 3], the function should return 4.

Given A = [−1, −3], the function should return 1.

Assume that:

N is an integer within the range [1..100,000];
each element of array A is an integer within the range [−1,000,000..1,000,000].
Complexity:

expected worst-case time complexity is O(N);
expected worst-case space complexity is O(N) (not counting the storage required for input arguments).

# Solution
```csharp
using System;
// you can also use other imports, for example:
// using System.Collections.Generic;

// you can write to stdout for debugging purposes, e.g.
// Console.WriteLine("this is a debug message");

class Solution {
    public int solution(int[] A) {
        // write your code in C# 6.0 with .NET 4.5 (Mono)
        
        Array.Sort(A);
        
        var len = A.Length - 1;
        
        var metOne = false;
        
        for (var i = 0; i < len; i++)
        {
            if (A[i] <= 0)
            {
                continue;   
            }
            
            if (A[i] == 1)
            {
                metOne = true;
            }
            
            if (A[i+1] != A[i] && (A[i + 1] - A[i]) != 1 && metOne)
            {
                return A[i] + 1;   
            }
        }
        
        if (!metOne && A[len] != 1)
        {
            return 1;    
        }
        
        return A[len] + 1;
    }
}
```
