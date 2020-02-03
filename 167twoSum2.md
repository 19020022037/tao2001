问题描述
--------------------
给定一个已按照升序排列 的有序数组，找到两个数使得它们相加之和等于目标数。

函数应该返回这两个下标值 index1 和 index2，其中 index1 必须小于 index2。

说明：
--------------------
返回的下标值（index1 和 index2）不是从零开始的。

你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。

示例
--------------------
输入: numbers = [2, 7, 11, 15], target = 9

输出: [1,2]

解释: 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 。

C程序
--------------------
```C
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* numbers, int numbersSize, int target, int* returnSize){
    int* index=(int *)malloc(sizeof(int)*2);
    for(int i=0;i<numbersSize;i++)
    for(int j=i+1;j<numbersSize;j++)
    {
        if(numbers[i]+numbers[j]==target){
            *returnSize=2;
            index[0]=i+1;
            index[1]=j+1;
            return index;
        }
    }
    *returnSize=0;
    return index;
}
```
