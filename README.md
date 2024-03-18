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
### 4) Ceil and Floor
```
public class Solution {
    public static int[] getFloorAndCeil(int[] arr, int n, int target) {
        int floor = -1;
        int ceil = -1;
        int start = 0;
        int end = n - 1;

        while(start<=end){
          int mid = start + (end - start) / 2;
            if(arr[mid] >= target){
                ceil = arr[mid];
                end = mid - 1;
            }
            else {
              start = mid + 1;
            }
        }

        start = 0;
        end = n-1;

        while(start<=end){
          int mid = start + (end - start) / 2;
            if(arr[mid] <= target){
                floor = arr[mid];
                start = mid + 1;
            }
            else {
              end = mid - 1;
            }
        }

        int[] ans = new int[2];
        ans[0] = floor;
        ans[1] = ceil;
        return ans;
    }
    
}
```
### 5) Find First and Last Position of Element in Sorted Array
```
class Solution {
    public int[] searchRange(int[] arr, int target) {
        int[] ans = {-1, -1};
        int n = arr.length;
        int first = -1;
        int last = n;
        int start = 0;
        int end = n - 1;
        while(start<=end){
            int mid = start + (end - start) / 2;
            if(arr[mid] >= target){
                first = mid;
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        }
        if(first == -1 || arr[first] != target) return ans;

        start = 0;
        end = n-1;

        while(start <= end){
            int mid = start + (end - start) / 2;
            if(arr[mid] > target){
                last = mid;
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        }
        ans[0] = first;
        ans[1] = last - 1;
        return ans;  
    }
}
```
### 6) Number of Occurences
```
public static int count(int arr[], int n, int target) {
        int first = -1, last = n;
        int start = 0, end = n-1;
        int count  = 0;

        while(start <= end){
            int mid = start + (end - start) / 2;
            if(arr[mid] >= target){
                first = mid;
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        }

        if(first==-1 || arr[first] != target) return count;

        start = 0;
        end = n-1;

        while(start <= end){
            int mid = start + (end - start) / 2;
            if(arr[mid] > target){
                last = mid;
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        }
        last -= 1;
        count = last - first;
        return count+1;
    }
```
### 7) Search in Rotated Sorted Array [Unique]
````
class Solution {
    public int search(int[] arr, int target) {
        int n = arr.length;
        int start = 0;
        int end = n-1;
        while(start <= end){
            int mid = start + (end - start) / 2;
            if(arr[mid] == target){
                return mid;
            }
            if(arr[start] <= arr[mid]){
                if(target >= arr[start] && target<= arr[mid]){
                    end = mid - 1;
                } else {
                    start = mid + 1;
                }
            } else {
                if(target >= arr[mid] && target<= arr[end]){
                    start = mid + 1;
                } else {
                    end = mid - 1;
                }
            }
        }
        return -1;
    }
}
```
