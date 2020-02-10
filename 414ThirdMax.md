问题描述
-----------------------
给定一个非空数组，返回此数组中第三大的数。如果不存在，则返回数组中最大的数。要求算法时间复杂度必须是O(n)。

示例
----------------------
示例 1:

输入: [3, 2, 1]

输出: 1

解释: 第三大的数是 1.

示例 2:

输入: [1, 2]

输出: 2

解释: 第三大的数不存在, 所以返回最大的数 2 .

示例 3:

输入: [2, 2, 3, 1]

输出: 1

解释: 注意，要求返回第三大的数，是指第三大且唯一出现的数。
存在两个值为2的数，它们都排第二。

C语言
--------------
```C
int thirdMax(int* nums, int numsSize){
    int min=nums[0],max=nums[0];
    for(int i=0;i<numsSize;i++)
    {
        if(nums[i]<min){
            min=nums[i];
        }
    }
    for(int i=0;i<numsSize;i++)
    {
        if(nums[i]>max){
            max=nums[i];
        }
    }
    int m=0;
    int comp(int* a,int* b)
    {
         return (*a)>(*b)?1:0;
    }
    qsort(nums,numsSize,sizeof(int),comp);
    for(int i=0;i<numsSize-1;i++)
    {
        if(nums[i]!=nums[i+1]){
            m++;
        }
    }
    if(m+1<3||numsSize<3){
        return max;
    }
    else{
        for(int j=0;j<numsSize;j++)
        {
            if(nums[j]==max){
                nums[j]=min;
                if(j==numsSize-1){
                    max=nums[j-1];
                }
                else{
                    max=nums[j+1];
                }
            }
        }
        for(int j=0;j<numsSize;j++)
        {
            if(nums[j]>max){
                max=nums[j];
            }
        }
        for(int j=0;j<numsSize;j++)
        {
            if(nums[j]==max){
                nums[j]=min;
                if(j==numsSize-1){
                    max=nums[j-1];
                }
                else{
                    max=nums[j+1];
                }
            }
        }
        for(int j=0;j<numsSize;j++)
        {
            if(nums[j]>max){
                max=nums[j];
            }
        }
        return max;
    }
}
