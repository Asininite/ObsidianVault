```java
class Solution {
    public int secondLargestElement(int[] nums) {
        int max = Integer.MIN_VALUE;
        int secondmax = Integer.MIN_VALUE;
        
        for(int i = 0; i < nums.length; i++){
            if(nums[i] > max){
                secondmax = max;
                max = nums[i];
            }
            if(nums[i] < max && nums[i] > secondmax){
                secondmax = nums[i];
            }
        }

        if(secondmax == Integer.MIN_VALUE){
            return -1;
        } else {
            return secondmax;
        }
    }
}
```