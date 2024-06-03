# 3. Longest Substring Without Repeating Characters 
**Medium**

Given a string `s`, find the length of the longest substring without repeating characters.

## Examples

### Example 1:
**Input:** `s = "abcabcbb"`

**Output:** `3`

**Explanation:** The answer is `"abc"`, with the length of 3.

### Example 2:
**Input:** `s = "bbbbb"`

**Output:** `1`

**Explanation:** The answer is `"b"`, with the length of 1.

### Example 3:
**Input:** `s = "pwwkew"`

**Output:** `3`

**Explanation:** The answer is `"wke"`, with the length of 3. Notice that the answer must be a substring, `"pwke"` is a subsequence and not a substring.

## Constraints:
- `0 <= s.length <= 5 * 10^4`
- `s` consists of English letters, digits, symbols and spaces.

## Solution O(n^2)

```csharp
public class Solution {
    public int LengthOfLongestSubstring(string s) {
        // Initialize maxLen result
        int maxLen = 0;

        // Iterate through each character of the string s
        for (int i = 0; i < s.Length; i++) {
            // Initialize visited[256] where all values are false
            bool[] visited = new bool[256]; 
            // Start iterating through possible substrings
            for (int j = i; j < s.Length; j++) {
                // If we there are no duplicates in this substring, we update the maxLen
                if (visited[s[j]] == false) {
                    // NOTE: j - i + 1 is the length of the current string
                    maxLen = Math.Max(maxLen, j - i + 1);
                    // Update the value of the current character in the visited[]
                    visited[s[j]] = true;
                }
                // If it is a duplicate we break and go to next i
                else {
                    break;
                }
            }
        }

        return maxLen;
    }
}
