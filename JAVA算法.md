# JAVA算法
## 1. 二分查找
每次取中间位置的值与待查关键字比较，如果中间位置的值比待查关键字大，则在前半部分循环这个查找的过程，如果中间位置的值比待查关键字小，则在后半部分循环这个查找的过程。直到查找到了为止，否则序列中没有待查的关键字。
```java
public static int bSearch(int[] arr, int a){
    int left=0;
    int right=arr.length-1;
    int mid;
    while(left<=right){
        mid = (left + right)/2;
        if(arr[mid]==a){
            return mid+1;
        }else if(arr[mid]<a){
            left = mid + 1;
        }else{
            right = mid - 1;
        }
    }
    return -1;
}
```

## 2. 冒泡排序
1. 比较前后相邻的二个数据，如果前面数据大于后面的数据，就将这二个数据交换。
2. 这样对数组的第 0 个数据到 N-1 个数据进行一次遍历后，最大的一个数据就“沉”到数组第 N-1 个位置。
3. N=N-1，如果 N 不为 0 就重复前面二步，否则排序完成。
```java
public static void bubbleSort(int [] a, int n){
    int i, j;
    for(i=0;i<n;i++){
        for(j=1;j<n-i;j++){
            if(a[j-1]>a[j]){
                int temp = a[j-1];
                a[j-1]=a[j];
                a[j]=temp;
            }
        }
    }
}

```

## 3. 插入排序
通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应的位置并插入。插入排序非常类似于整扑克牌。在开始摸牌时，左手是空的，牌面朝下放在桌上。接着，一次从桌上摸起一张牌，并将它插入到左手一把牌中的正确位置上。为了找到这张牌的正确位置，要将它与手中已有的牌从右到左地进行比较。无论什么时候，左手中的牌都是排好序的。

如果输入数组已经是排好序的话，插入排序出现最佳情况，其运行时间是输入规模的一个线性函数。如果输入数组是逆序排列的，将出现最坏情况。平均情况与最坏情况一样，其时间代价是(n2)。
```java
public void sort(int arr[]){
    for(int i=1;i<arr.length;i++){
        int insertVal = arr[i];
        int index = i-1;
        while(index>=0&&insertVal<arr[index]){
            arr[index+1]=arr[index];
            index--;
        }
        arr[index+1]=insertVal;
    }
}
```

## 4. 快速排序
选择一个关键值作为基准值。比基准值小的都在左边序列(一般是无序的)，比基准值大的都在右边(一般是无序的)。一般选择序列的第一个元素。

```java
public void sort(int[] a, int low, int high){
    int start = low;
    int end = high;
    int key=a[low];
    while(start<end){
        while(start<end&&a[end]>=key){
            end--;
            if(a[end]<=key){
                int tmp = a[end];
                a[end] = a[start];
                a[start] = tmp;
            }
            
        }
        while(start<end&&a[start]<=key){
            start++;
            if(a[start]>=key){
                int tmp = a[start];
                a[start] = a[end];
                a[end] = tmp;
            }
        }

    }
    if(start>low){
        sort(a,low,start-1);
    }
    if(end<high){
        sort(a,end+1,high);
    }
}
```
## 5. 希尔排序
## 6. 归并排序
将两个(或两个以上)有序表合并成一个新的有序表，即把待排序序列分为若干个子序列，每个子序列是有序的。然后再把有序子序列合并为整体有序序列。
```java
public class MergeSort{
    public staic void mergeSort(int[] data){
        sort(data, 0, data.length - 1);
    }
    public static void sort(int[] data, int left, int right){
        if(left>=right){
            return;
        }
        int center = (left+right)/2;
        sort(data, left, center);
        sort(data, center+1, right);
        merge(data, left, center, right);
    }
    public static void merge(int[] data, int left, int center, int right){
        int[] tmpArr = new int[data.length];
        int mid = center + 1;
        int third = left;
        int tmp = left;
        while (left <= center && mid <= right){
            if (data[left] <= data[mid]) {
                tmpArr[third++] = data[left++]; 
            } else {
                tmpArr[third++] = data[mid++]; 
            }
        }
        while (mid <= right) {
            tmpArr[third++] = data[mid++];
        }
        while(left<=center){
            tmpArr[third++] = data[left++]; 
        }
        while (tmp <= right) {
            data[tmp++] = tmpArr[tmp++]; 
        }

    }
}
```

## 7. 剪枝算法
在搜索算法中优化中，剪枝，就是通过某种判断，避免一些不必要的遍历过程，形象的说，就是剪去了搜索树中的某些“枝条”，故称剪枝。应用剪枝优化的核心问题是设计剪枝判断方法，即确定哪些枝条应当舍弃，哪些枝条应当保留的方法。

## 8. 回溯算法
回溯算法实际上一个类似枚举的搜索尝试过程，主要是在搜索尝试过程中寻找问题的解，当发现已不满足求解条件时，就“回溯”返回，尝试别的路径。








