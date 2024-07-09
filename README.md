
# DSA-PROBLEMS

## Find the Largest element in an array [click here](https://www.naukri.com/code360/problems/largest-element-in-the-array-largest-element-in-the-array_5026279?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems)
**Approach:**
1. assume a[0]= larger.
2. compare with other element.
3. a[i]>larger .print a[i]= largest.
  
**SOLUTION:** IN JAVA
```java
import java.util.* ;
import java.io.*; 

public class Solution {

    static int largestElement(int[] arr, int n) {
        int largestElement=arr[0];
        for(i =0,i<n-1;i++){
            largestElement=arr[i];

        }
        print(largestElement)

    }
}
```

Time Complexity:  **O(n)**
Space Complexity:  **O(1)**

[**Refer this**](https://youtu.be/37E9ckMDdTk?si=wHRlktwzjngsqNuk)


