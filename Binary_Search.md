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
            if(target < a[mid]) 
	    	end=mid-1;
            else if (target > a[mid])
	    	start = mid+1;
	    else
	    	return mid;
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

### 5. Find position of an element in a sorted array of infinite numbers
![image](https://user-images.githubusercontent.com/63279839/150290832-8a9e1fb9-af15-4675-8989-267b70fbf359.png)

![image](https://user-images.githubusercontent.com/63279839/150291441-27133f21-7d80-45b0-9f67-37274513ed59.png)
![image](https://user-images.githubusercontent.com/63279839/150291753-c59a7e41-5bec-4888-a35b-af1866029410.png)

```
public class InfiniteArray {
    public static void main(String args[]) {
      int[] arr={3,5,7,9,10,90,100,130,140,160,170};
      int target = 90;
      System.out.println(ans(arr,target));
    }
    static int ans(int[] arr, int target) {
        int start = 0;
        int end = 1;
        
        //condition for the target to lie in the range
        while (target > arr[end]) {
            int temp = end + 1;
            //double the box value
            end = end + (end - start + 1) * 2;
            start = temp;
        }
        return binarySearch(arr,target,start,end);
    }
    static int binarySearch(int[] a, int target,int start, int end) {
        while(start <= end) {
            int mid=start+(end-start)/2;
            if(target < a[mid]) 
	    	end=mid-1;
            else if (target > a[mid])
	    	start = mid+1;
	        else
	    	    return mid;
        }
        return -1;
    }
}
```
### 6. Peak Index in a Mountain Array
https://leetcode.com/problems/peak-index-in-a-mountain-array/
![image](https://user-images.githubusercontent.com/63279839/150391058-8f6006f0-f32a-4269-96d6-91a0f5b2d132.png)
![image](https://user-images.githubusercontent.com/63279839/150391390-197bce91-6abe-4d5a-9745-7ea851543b88.png)
![image](https://user-images.githubusercontent.com/63279839/150391687-22cdefd7-9576-44ef-98ba-ec2d0b386e18.png)
![image](https://user-images.githubusercontent.com/63279839/150391883-e919e5bf-b803-4ab8-8e39-9142bcea953e.png)

**Solution:**
```
class Solution {
    public int peakIndexInMountainArray(int[] arr) {
        int start = 0;
        int end = arr.length - 1;
        while (start < end) {
            int mid = start + (end - start) / 2;
            
            if(arr[mid] > arr[mid+1])
                end = mid;
            else if(arr[mid] < arr[mid+1])
                start = mid + 1;
        }
        return start;
    }
}
```
