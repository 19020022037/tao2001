问题描述
----------------------
给定一个长度为 n 的整数数组，你的任务是判断在最多改变 1 个元素的情况下，该数组能否变成一个非递减数列。

我们是这样定义一个非递减数列的： 对于数组中所有的 i (1 <= i < n)，满足 array[i] <= array[i + 1]。

示例
-------------
示例 1:

输入: [4,2,3]

输出: True

解释: 你可以通过把第一个4变成1来使得它成为一个非递减数列。

示例 2:

输入: [4,2,1]

输出: False

解释: 你不能在只改变一个元素的情况下将其变为非递减数列。

说明:
--------------------
n 的范围为 [1, 10,000]。

C语言
------------------
```C
bool checkPossibility(int* nums, int numsSize){
    if(numsSize==2){
        return true;
    }
    int min=nums[0],max=nums[0],temp1=0,temp2=0,temp3=0,temp4=0,m=0;
    for(int i=0;i<numsSize;i++)
    {
        if(min >= nums[i]){
            min = nums[i];
            temp1 = i;
        }
        if(max <= nums[i]){
            max = nums[i];
            temp2 = i;
        }
    }
    for(int i=0;i<numsSize-1;i++)
    {
        if(nums[i]<=nums[i+1]){
           temp3++; 
        }
        else{
            temp4++;
            m=i;
        }
    }
    if((temp3==numsSize-1)||(temp3==numsSize-2&&temp4==1&&m!=0&&m!=numsSize-1&&m!=numsSize-2&&((nums[m+2]>=nums[m]&&nums[m-1]<=nums[m])||(nums[m+2]>=nums[m+1]&&nums[m-1]<=nums[m+1])))||(temp3==numsSize-2&&temp4==1&&(m==0||m==numsSize-2))){
        return true;
    }
    int t=0;
    if(temp1==1&&temp2!=numsSize-2){
        for(int i=2;i<numsSize-1;i++){
            if(nums[i]<=nums[i+1]){
                t=0;    
            }
            else{
                t=1;
                break;
            }
        }
        if(t==0){
            return true;
        }
    }
    if(temp1!=1&&temp2==numsSize-2){
        for(int i=0;i<numsSize-2;i++){
            if(nums[i]<=nums[i+1]){
                t=0;    
            }
            else{
                t=1;
                break;
            }
        }
        if(t==0){
            return true;
        }
    }
    return false;
}
