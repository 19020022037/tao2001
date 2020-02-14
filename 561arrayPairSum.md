题目描述
------------------------

给定长度为 2n 的数组, 你的任务是将这些数分成 n 对, 例如 (a1, b1), (a2, b2), ..., (an, bn) ，使得从1 到 n 的 min(ai, bi) 总和最大。

示例
---------------

示例 1:

输入: [1,4,3,2]

输出: 4

解释: n 等于 2, 最大总和为 4 = min(1, 2) + min(3, 4).

提示:
---------------

n 是正整数,范围在 [1, 10000].
	
  数组中的元素范围在 [-10000, 10000].

C语言
---------------
```C
int arrayPairSum(int* nums, int numsSize){
    /*for(int i=0;i<numsSize;i++)
    for(int j=i+1;j<numsSize;j++)
    {
        if(nums[i]>nums[j]){
            int temp=nums[i];
            nums[i]=nums[j];
            nums[j]=temp;
        }
    }*/
    int cmp(const void *a, const void *b)
    {
	return *(int*)a > *(int*)b;
    }
    qsort(nums, numsSize, sizeof(int), cmp);
    int sum=0;
    for(int i=0;i<numsSize/2;i++)
    {
        sum=nums[2*i]+sum;
    }
    return sum;
}
