问题描述
--------------------
给定一个整数数组，判断是否存在重复元素。

如果任何值在数组中出现至少两次，函数返回 true。如果数组中每个元素都不相同，则返回 false。

示例
-------------------
示例 1:

输入: [1,2,3,1]

输出: true

示例 2:

输入: [1,2,3,4]

输出: false

示例 3:

输入: [1,1,1,3,3,4,3,2,4,2]

输出: true

C语言
---------------
```C
bool containsDuplicate(int* nums, int numsSize){
    /*for(int i=0;i<numsSize;i++)
    {
        for(int j=0;j<numsSize;j++)
        {
            if(nums[j]==nums[i]&&j!=i){
                return true;
            }
        }
    }
    return false;*/                    错误原因：超出额外时间；
    /*for(int i=0;i<numsSize;i++)
    for(int j=i+1;j<numsSize;j++)
    {
        if(nums[i]>nums[j]){
            long int temp=nums[i];
            nums[i]=nums[j];
            nums[j]=temp;
        }
    }
    for(int i=0;i<numsSize-1;i++)
    {
        if(nums[i]==nums[i+1]){
            return true;
        }
    }
    return false;*/                   错误原因：超出额外时间；
    
    
    int comp(const void*a,const void*b)
    {
        return *(int*)a-*(int*)b;
    }
    qsort(nums,numsSize,sizeof(int),comp);
    for(int i=0;i<numsSize-1;i++)
    {
        if(nums[i]==nums[i+1]){
            return true;
        }
    }
    return false;
}
```
