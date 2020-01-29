问题描述
---------------
给定两个有序整数数组 nums1 和 nums2，将 nums2 合并到 nums1 中，使得 num1 成为一个有序数组。

说明:  
初始化 nums1 和 nums2 的元素数量分别为 m 和 n。  
你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。

示例
----------------
输入:
nums1 = [1,2,3,0,0,0], m = 3  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;nums2 = [2,5,6],&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;n = 3

输出: [1,2,2,3,5,6]

C语言
-----------------
```C
void merge(int* nums1, int nums1Size, int m, int* nums2, int nums2Size, int n){
    int i=m,j=0;
    while(i<n+m){
        nums1[i]=nums2[j];
        i++;
        j++;
    }
    for(int i=0;i<n+m;i++)
    for(int j=i+1;j<n+m;j++)
    {
        if(nums1[i]>nums1[j]){
            int temp=nums1[i];
            nums1[i]=nums1[j];
            nums1[j]=temp;
        }
    }
    return;
}
```
