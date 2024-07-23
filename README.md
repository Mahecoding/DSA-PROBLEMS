<img src="dsa logo.png"/>


# DSA-PROBLEMS

**TOPIC: ARRAY**

## 1. Find the Largest element in an array [click here](https://www.naukri.com/code360/problems/largest-element-in-the-array-largest-element-in-the-array_5026279?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems)
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
        for(i =0;i<n-1;i++){
            largestElement=arr[i];

        }
        print(largestElement)

    }
}
```

1.Time Complexity:  **O(n)** <br/>
2. Space Complexity:  **O(1)**

[**Refer this**](https://youtu.be/37E9ckMDdTk?si=wHRlktwzjngsqNuk)
--
## 4. Left Rotate the Array by One[click here](https://www.naukri.com/code360/problems/left-rotate-an-array-by-one_5026278?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems&leftPanelTabValue=SUBMISSION)
**Approach:**
1. take a[0] as temp
2. iterate the array from the 0th index to the n-1th index(to prevent its segmentation fault we will iterate it till n-1.)
3. put the value of temp  in the last index of the array.(a[n-1])
<img src="movearrayby1.png"/>

**SOLUTION:** IN JAVA
```java
import java.util.* ;
import java.io.*; 


public class Solution {

    static int[] rotateArray(int[] arr, int n)
     {
       int temp=arr[0];
       for(int i=0;i<n-1;i++){
           arr[i]=arr[i+1];
       }
       arr[n-1]=temp;
       return arr;

    
  
     }
}
```

1.Time Complexity:  **O(n)** <br/>
2. Space Complexity:  **O(1)**

[**Refer this**](https://youtu.be/wvcQg43_V8U?si=FZ6ZdKo2Kyw7alht)

---
## 4. Move Zero's to End [click here](https://www.naukri.com/code360/problems/ninja-and-the-zero-s_6581958?utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_Arrayproblems)


**Approach: BRUTE FORCE  (the use of an extra array)**

There are **N-X** zeros  **X** non-zero elements in the array.
1. Set temp=[] 
2. first copy those X non-zero elements from the original array to a temporary array. 
3. then, copy the elements from the temp array one by one .Fill the first X places of the original array.
4. The last N-X places of the original array will be then filled with zero.
  
**SOLUTION:** IN JAVA
```java
import java.util.ArrayList;

public class Solution {
        public static int[] moveZeros(int n, int []a) {

            ArrayList<Integer> temp = new ArrayList<>();
            for(int i= 0;i<n;i++){
                if(a[i]!= 0){
                    temp.add(a[i]);
                }
            }
            int nz= temp.size();
            for(int i=0;i< nz;i++){
                a[i]=temp.get(i);
            }
      for ( int i= nz; i<n;i++){
          a[i] = 0;
      }
      return a;
    }
}
```

1.Time Complexity:  **O(N) + O(X) + O(N-X) = O(2*N)** <br/>
**Reason:** 
1. O(N) for copying non-zero elements from the original to the temporary array. 
2. O(X) for again copying it back from the temporary to the original array. 
3. O(N-X) for filling zeros in the original array.

2. Space Complexity:  **O(N)** -using a temporary array

[**Refer this**](https://youtu.be/wvcQg43_V8U?si=QigzAGQ6Ag72bsn7)

---

**Approach: OPTIMAL SOLUTION**
1. Initialize Variables:

Set a variable j to -1. This will be used to track the position of the first zero found.

2. Find the First Zero:

Loop through the array from the beginning to the end.
Check each element to see if it is zero.
Once you find the first zero, record its index in j and stop the loop (using break).

3. Check If No Zero Found:

After the loop, if j is still -1, it means there were no zeros in the array.
If this is the case, return the array as it is because there’s nothing to move.

4. Move Non-Zero Elements:

Start a second loop from the index right after the first zero (j + 1) to the end of the array.
For each element in this range, if it is not zero, swap it with the element at index j (the position of the first zero found).
After swapping, increment j to point to the next zero position.

5. Return the Modified Array:

After completing the second loop, return the modified array where all zeros have been moved to the end.
  
**SOLUTION:** IN JAVA
```java
public class Solution {
    // This is the class declaration for the class named Solution.
    
    public static int[] moveZeros(int n, int[] a) {
        // This is a method named moveZeros that is public (accessible from outside the class) and static (belongs to the class rather than an instance of the class).
        // The method returns an array of integers.
        // The method takes two parameters: an integer 'n' (the length of the array) and an integer array 'a'.

        int j = -1;
        // Initialize an integer variable 'j' to -1. This variable will be used to keep track of the position of the first zero found in the array.

        for (int i = 0; i < n; i++) {
            // Start a for loop that iterates from 0 to n-1.
            if (a[i] == 0) {
                // Check if the current element of the array 'a' is zero.
                j = i;
                // If a zero is found, set 'j' to the current index 'i'.
                break;
                // Break out of the loop since the position of the first zero has been found.
            }
        }

        if (j == -1) return a;
        // If 'j' is still -1 after the loop, it means there were no zeros in the array.
        // In this case, return the array 'a' as it is.

        for (int i = j + 1; i < n; i++) {
            // Start another for loop that iterates from the position just after the first zero found ('j + 1') to the end of the array.
            if (a[i] != 0) {
                // Check if the current element of the array 'a' is not zero.
                int temp = a[i];
                // Store the current element in a temporary variable 'temp'.
                a[i] = a[j];
                // Move the zero from position 'j' to the current position 'i'.
                a[j] = temp;
                // Move the non-zero element from the current position 'i' to position 'j'.
                j++;
                // Increment 'j' to point to the next zero position.
            }
        }

        return a;
        // Return the modified array 'a' after moving all zeros to the end.
    }
}

```


1. Time Complexity: O(N), N = size of the array.
Reason: We have used 2 loops and using those loops, we are basically traversing the array once.
<br/>

2. Space Complexity: O(1) as we are not using any extra space to solve this problem.

[**Refer this**](https://youtu.be/wvcQg43_V8U?si=QigzAGQ6Ag72bsn7)








