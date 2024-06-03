# 2486. Append Characters to String to Make Subsequence

You are given two strings s and t consisting of only lowercase English letters.

Return the minimum number of characters that need to be appended to the end of s so that t becomes a subsequence of s.

A subsequence is a string that can be derived from another string by deleting some or no characters without changing the order of the remaining characters.

## Example 1:

**Input:** s = "coaching", t = "coding"
**Output:** 4
**Explanation:** Append the characters "ding" to the end of s so that s = "coachingding".
Now, t is a subsequence of s ("coachingding").
It can be shown that appending any 3 characters to the end of s will never make t a subsequence.

## Example 2:

**Input:** s = "abcde", t = "a"
**Output:** 0
**Explanation:** t is already a subsequence of s ("abcde").

## Example 3:

**Input:** s = "z", t = "abcde"
**Output:** 5
**Explanation:** Append the characters "abcde" to the end of s so that s = "zabcde".
Now, t is a subsequence of s ("zabcde").
It can be shown that appending any 4 characters to the end of s will never make t a subsequence.

## Constraints:

- 1 <= s.length, t.length <= 105
- s and t consist only of lowercase English letters.

## Solution
### Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Since I had to find the number of characters needed for t to be a subsequence of s, initially, I thought of determining the maximum number of characters, starting from the first character of t, that are already a subsequence of s. This way, I could identify the characters in t that are already present in s and quickly find out the number of characters needed for the answer.


### Approach
<!-- Describe your approach to solving the problem. -->
To solve this problem, I implemented a solution that iterates through both strings, s and t. The goal was to find how many characters of t, in ascending order, are already present in s in ascending order.

For each character in t, I searched for its occurrence in s. If a match was found, I advanced both indices to the next character in s and t. If no match was found, I advanced only the index in s, as we're looking for a subsequence and the order of characters matters.

After iterating through both strings, I returned the difference between the length of t and the index of t. This represents the number of characters in t that are not yet part of the subsequence formed by s.



### Complexity
- Time complexity:
O(Max(s.Length, t.Length))

- Space complexity:
O(1)

### Code
```csharp
public class Solution {
    public int AppendCharacters(string s, string t) {
        // Initialize indices for iterating through strings s and t
        int s_index = 0;
        int t_index = 0;

        // Iterate through s and t to find matching characters
        while (s_index < s.Length && t_index < t.Length) {
            // If a matching character is found, advance both indices
            if (s[s_index] == t[t_index]) {
                s_index++; // Move to the next character in s
                t_index++; // Move to the next character in t
            }
            // If no match is found, advance the index in s
            else {
                s_index++; // Move to the next character in s
            }
        }
        
        // Calculate the number of characters in t that are not part of the subsequence in s
        int charactersToAdd = t.Length - t_index;

        // Return the difference between the length of t and the number of t characters already in s
        return charactersToAdd;
    }
}

```
