## Binary Search

### Binary Search

```
public class MyClass {
    public static void main(String args[]) {
      int a[] = {1,4,6,7,8};
      int key = 5;
      int ans = BS(a,key);
      System.out.println(ans);
    }
    static int BS(int[] a, int target) {
        int start = 0;
        int end = a.length -1;
        while(start<=end) {
            int mid=start+(end-start)/2;
            if(a[mid]==target) return mid;
            else if(target < a[mid]) end=mid-1;
            else start = mid+1;
        }
        return -1;
    }
}
```

### Agnostic Binary Search

```
public class MyClass {
    public static void main(String args[]) {
      int a[] = {10,9,8,6,5};
      int key = 5;
      int ans = ABS(a,key);
      System.out.println(ans);
    }
    static int ABS(int[] a, int key) {
        int start=0;
        int end=a.length -1;
        boolean asc=a[start]<a[end];
        while(start<=end) {
            int mid=start+(end-start)/2;
            if(a[mid]==key) return mid;
            if(asc) {
                if(key < a[mid]) end=mid-1;
                else start = mid+1;
            } else {
                if(key > a[mid]) end=mid-1;
                else start = mid+1;
            }
        }
        return -1;
    }
}
```


## Problems 
### 1. Ceiling of a number
```
if( target > arr[arr.length-1] ){
	return -1;
}
return start; //at last
```

### 2. Floor of a number
```
return end; //at last
```
### 3. Find Smallest Letter Greater Than Target 

https://leetcode.com/problems/find-smallest-letter-greater-than-target/

![image](https://user-images.githubusercontent.com/63279839/150173861-4c6c6f79-b166-48cd-92fc-c43cf74af42e.png)
![image](https://user-images.githubusercontent.com/63279839/150173692-739ac95a-14d9-43b5-b215-75a734f07d96.png)


**Solution:**
```
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        int start=0;
        int end=letters.length -1;
        while(start<=end) {
            int mid=start+(end-start)/2;
            if(target < letters[mid]) 
                end=mid-1;
            else 
                start = mid+1;
        }
        return letters[start % letters.length];
    }
}
```

### 4. Find First and Last Position of Element in Sorted Array
https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/

![image](https://user-images.githubusercontent.com/63279839/150178324-7c3a3e33-aaa2-4c0d-aee7-e1c49dd11517.png)

**Solution:**
```
class Solution {
    public int[] searchRange(int[] nums, int target) {
        
        int[] ans = {-1,-1};   
        
        //check for first occurrence of target first
        int start = search(nums,target,true);
        int end = search(nums,target,false);
        
        ans[0]=start;
        ans[1]=end;
        
        return ans;
    }
    
    int search(int[] nums, int target, boolean findStartIndex) {
        int ans = -1;
        int start = 0;
        int end = nums.length -1;
        
        while(start <= end) {
            int mid=start+(end-start)/2;
            
            if(target < nums[mid]) 
                end = mid - 1;
            else if (target > nums[mid]) 
                start = mid + 1;
            else { 
                ans= mid; 
                if (findStartIndex)
                    end = mid - 1;
                else
                    start = mid + 1;
            }
        }
        return ans;
    }
}
```

![image](https://user-images.githubusercontent.com/63279839/150181285-5d7f56c9-ecb5-4dd1-a72b-428aa53a9ded.png)
