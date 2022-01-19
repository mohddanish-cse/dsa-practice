###Agnostic Binary Search

public class MyClass {
    public static void main(String args[]) {
      int a[] = {10,9,8,6,5};
      int key =5;
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


Problems 
Ceiling of a number

	if( target > arr[arr.length-1] ){
		return -1;
	}
return start; //at last


Floor of a number
return end; //at last

Find Smallest Letter Greater Than Target https://leetcode.com/problems/find-smallest-letter-greater-than-target/



Solution:
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





