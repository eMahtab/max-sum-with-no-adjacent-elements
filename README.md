# Max sum with no adjacent elements
Given an array of positive integers find the **maximum sum of non-adjacent elements** in the array. If a sum cannot be generated, return 0.

#### Note : We can not include two adjacent numbers.


**Example 1:**

Input: [2,3,2]

Output: 3 (include only the second number)

**Example 2:**

Input: [1,2,3,1]

Output: 4 (include the first and third number)


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

Time Complexity  = O(n)
Space Complexity = O(n)

