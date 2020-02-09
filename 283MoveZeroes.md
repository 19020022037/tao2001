问题描述
--------------------
给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。

示例
------------------
示例:

输入: [0,1,0,3,12]

输出: [1,3,12,0,0]

说明:
-------------------
必须在原数组上操作，不能拷贝额外的数组。
尽量减少操作次数。

C语言
-------------------
```C
class Solution:
void moveZeroes(int* nums, int numsSize){
    int temp=0;
    for(int i=0;i<numsSize;i++)
    {
        if(nums[i]==0){
            temp++;
        }
    }
    int j=0;
    for(int i=0;i<numsSize;i++)
    {
        if(nums[i]!=0){
            nums[j]=nums[i];
            j++;
        }
    }
    for(int i=numsSize-temp;i<numsSize;i++)
    {
        nums[i]=0;
    }
    return;
}
```
