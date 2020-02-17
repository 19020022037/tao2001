问题描述
-----------------
给定一个整型数组，在数组中找出由三个数组成的最大乘积，并输出这个乘积。

示例
-------------
示例 1:

输入: [1,2,3]

输出: 6

示例 2:

输入: [1,2,3,4]

输出: 24

注意:
--------------------
给定的整型数组长度范围是[3,10的4次方]，数组中所有的元素范围是[-1000, 1000]。
  
输入的数组中任意三个数的乘积不会超出32位有符号整数的范围。

C语言
------------------
```C
int maximumProduct(int* nums, int numsSize){
     int cmp(const void *a, const void *b)
    {
	return *(int*)a < *(int*)b;
    }
    qsort(nums, numsSize, sizeof(int), cmp);
    if(nums[0]*nums[1]*nums[2]>nums[0]*nums[numsSize-1]*nums[numsSize-2])
    {
        return nums[0]*nums[1]*nums[2];
    }
    else{
        return nums[0]*nums[numsSize-1]*nums[numsSize-2];
    }
}
