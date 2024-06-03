# 3110. Score of a String (Easy)

You are given a string s. The score of a string is defined as the sum of the absolute difference between the ASCII values of adjacent characters.

Return the score of s.

### Example 1:

Input: s = "hello"

Output: 13

Explanation:

The ASCII values of the characters in s are: 'h' = 104, 'e' = 101, 'l' = 108, 'o' = 111. So, the score of s would be |104 - 101| + |101 - 108| + |108 - 108| + |108 - 111| = 3 + 7 + 0 + 3 = 13.

### Example 2:

Input: s = "zaz"

Output: 50

Explanation:

The ASCII values of the characters in s are: 'z' = 122, 'a' = 97. So, the score of s would be |122 - 97| + |97 - 122| = 25 + 25 = 50.

### Constraints:

- 2 <= s.length <= 100
- s consists only of lowercase English letters.

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
