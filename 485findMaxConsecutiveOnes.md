问题描述
--------------------
给定一个二进制数组， 计算其中最大连续1的个数。

示例
--------------------
示例 1:

输入: [1,1,0,1,1,1]

输出: 3

解释: 开头的两位和最后的三位都是连续1，所以最大连续1的个数是 3.

注意：
------------------
输入的数组只包含 0 和1。
输入数组的长度是正整数，且不超过 10,000。

C语言
-------------------
```C
int findMaxConsecutiveOnes(int* nums, int numsSize){
    int a[numsSize+1];
    a[numsSize]=0;
    for(int i=0;i<numsSize;i++)
    {
        a[i]=nums[i];
    }
    int k=0,max=0,temp=0;
    for(int i=0;i<numsSize+1;i++)
    {
        if(a[i]==0){
            temp=i-k;
            k=i+1;
            if(temp>max){
                max=temp;
            }
        }
    }
    return max;
}
