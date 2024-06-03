# Intuition
Pretty straight-forward, my initial approach was to iterate through the string, calculate the absolute difference between adjacent characters, and accumulate the sum to get the final score.

# Approach
1. Initialize a variable res to store the result, starting with 0.
2. Iterate through the string from index 0 to s.Length - 2.
3. For each pair of adjacent characters, calculate the absolute difference between their ASCII values and add it to res.
4. Return res as the final score.

# Complexity
- Time complexity:
$$O(n)$$

- Space complexity:
$$O(1)$$

# Code
```csharp
public class Solution {
    public int ScoreOfString(string s) {
        int res = 0;
        for (int i = 0; i < s.Length - 1; i++) {
            res += Math.Abs(s[i] - s[i+1]);
        }
        return res;
    }
}
```
