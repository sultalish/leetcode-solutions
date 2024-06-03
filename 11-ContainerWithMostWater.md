# [11. Container With Most Water](https://leetcode.com/problems/container-with-most-water/description/)

## Solution O(n^2)
```csharp
public class Solution {
    public int MaxArea(int[] height) {
        int maxWater = 0;
        for (int i = 0; i < height.Length; i++) {
            for (int j = i + 1; j < height.Length; j++) {
                if (Math.Min(height[i], height[j]) * (j - i) > maxWater) {
                    maxWater = Math.Min(height[i], height[j]) * (j - i);
                }
            }
        }

        return maxWater;
    }
}
```

## Solution O(n)
```csharp
public class Solution {
    public int MaxArea(int[] height) {
        int maxWater = 0;
        int left = 0;
        int right = height.Length - 1;
        while (left < right) {
            int curWater = Math.Min(height[left], height[right]) * (right - left);
            if (curWater > maxWater) {
                maxWater = curWater;
                curWater = 0;
            }

            if (height[left] > height[right]) {
                right--;
            }
            else {
                left++;
            }

        }

        return maxWater;
    }
}
```
