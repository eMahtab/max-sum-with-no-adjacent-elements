# Max sum with no adjacent elements
Given an array of positive integers find the **maximum sum of non-adjacent elements** in the array. If a sum cannot be generated, return 0.

#### Note : We can not include two adjacent numbers.


**Example 1:**

Input: [2,3,2]

Output: 3 (include only the second number)

**Example 2:**

Input: [1,2,3,1]

Output: 4 (include the first and third number)


# Related Question 
https://leetcode.com/problems/house-robber/


### Dynamic Programming Implementation

```java
public int maxSubsetSumNoAdjacent(int[] array) {
    if(array == null || array.length == 0){
	return 0;
    } else if (array.length == 1){
        return array[0];
    } 
        
    int length = array.length;
    int[] maxSums = new int[length];
    maxSums[0] = array[0];
    maxSums[1] = Math.max(array[0], array[1]);
			
    for(int i = 2; i < length; i++){
	maxSums[i] = Math.max(maxSums[i-1], maxSums[i-2] + array[i]);
    }
		
    return maxSums[length-1];
}
```

Both the time and space complexity of above dynamic programming implementation is O(n)
```
Time Complexity  = O(n)
Space Complexity = O(n)
```

### Dynamic Programming Implementation - Space Optimization O(1)

```java
public int maxSubsetSumNoAdjacent(int[] array) {
    if(array == null || array.length == 0){
	return 0;
    } else if (array.length == 1){
        return array[0];
    } 
        
    int length = array.length;
    int prev_prev_max_sum = array[0];
    int prev_max_sum = Math.max(array[0], array[1]);	
    int maxSum = prev_max_sum;
    
    for(int i = 2; i < length; i++){
	maxSum = Math.max(prev_max_sum, prev_prev_max_sum + array[i]);
	prev_prev_max_sum = prev_max_sum;
	prev_max_sum = maxSum;
    }
		
    return maxSum;
}
```

Above implementation have time complexity of O(n) but space complexity of O(1)
```
Time Complexity  = O(n)
Space Complexity = O(1)
```


