# Binary Search - 1 Dim
### 1) Lower Bound
hint: arr[ind] >= target and also make sure the index is lowest
```
class Solution {
    public int lowerBound(int[] arr, int target) {
        int n = arr.length;
        int ans = n;
        int start = 0;
        int end = n-1;
        while(start<=end){
            int mid = start + (end - start) / 2;
            if(arr[mid] >= target){
                end = mid - 1;
                ans = mid;
            } else {
                start = mid+1;
            }
        }
        return ans;
    }
}
```
### 2) Upper Bound
hint: arr[ind] > target and also make sure the index is lowest
```
class Solution {
    public int upperBound(int[] arr, int target) {
        int n = arr.length;
        int ans = n;
        int start = 0;
        int end = n-1;
        while(start<=end){
            int mid = start + (end - start) / 2;
            if(arr[mid] > target){
                end = mid - 1;
                ans = mid;
            } else {
                start = mid+1;
            }
        }
        return ans;
    }
}
```
### 3) Select Insert Position
hint: Just implement the lower bound
```
class Solution {
    public int searchInsert(int[] arr, int target) {
        int n = arr.length;
        int ans = n;
        int start = 0;
        int end = n-1;
        while(start<=end){
            int mid = start + (end - start) / 2;
            if(arr[mid] >= target){
                end = mid - 1;
                ans = mid;
            } else {
                start = mid+1;
            }
        }
        return ans;
    }
}
```
