问题描述
-------------

给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

示例
-------------

输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。

C语言解决办法
--------------
```c
int maxSubArray(int* nums, int numsSize){
    int sum=0;
    for(int i=0;i<numsSize;i++)
    {
        sum=sum+nums[i];
    }
    int max=sum,temp=sum,t=0;
    for(int i=numsSize-1;i>0;i--)
    {
        for(int j=0;j<numsSize-t-1;j++)
        {
            sum=sum-nums[j];
            if(max<sum){
                max=sum;
            }
        }
        sum=temp-nums[i];
        if(max<sum){
                max=sum;
        }
        temp=sum;
        t++;
    }
    return max;
}
```
