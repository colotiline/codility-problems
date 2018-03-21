# Task
A zero-indexed array A consisting of N different integers is given. The array contains integers in the range [1..(N + 1)], which means that exactly one element is missing.

Your goal is to find that missing element.

Write a function:

class Solution { public int solution(int[] A); }

that, given a zero-indexed array A, returns the value of the missing element.

For example, given array A such that:

  A[0] = 2
  A[1] = 3
  A[2] = 1
  A[3] = 5
the function should return 4, as it is the missing element.

Assume that:

N is an integer within the range [0..100,000];
the elements of A are all distinct;
each element of array A is an integer within the range [1..(N + 1)].
Complexity:

expected worst-case time complexity is O(N);
expected worst-case space complexity is O(1), beyond input storage (not counting the storage required for input arguments).

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
        
        if (A.Length == 0)
        {
            return 1;
        }
        
        if (A.Length == 1) 
        {
            return A[0] == 1 ? 2 : 1;
        }
        
        Array.Sort(A);
        
        if (A[0] != 1)
        {
            return 1;
        }
        
        for (var i = 1; i < A.Length; i++) 
        {
            var diff = A[i] - A[i-1];
            
            if (diff != 1 && diff != 0)
            {
                return A[i] - 1;
            }
        }
        
        return A[A.Length - 1] + 1;
    }
}
```
