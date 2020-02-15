问题描述
--------------

给定一个整数数组，你需要寻找一个连续的子数组，如果对这个子数组进行升序排序，那么整个数组都会变为升序排序。

你找到的子数组应是最短的，请输出它的长度。

示例
-------------------
示例 1:

输入: [2, 6, 4, 8, 10, 9, 15]

输出: 5

解释: 你只需要对 [6, 4, 8, 10, 9] 进行升序排序，那么整个表都会变为升序排序。

说明 :
---------------------

 输入的数组长度范围在 [1, 10,000]。
	
 输入的数组可能包含重复元素 ，所以升序的意思是<=。
  
C语言
------------------------
```C
int findUnsortedSubarray(int* nums, int numsSize){
    int a[numsSize];
    for(int i=0;i<numsSize;i++)
    {
        a[i]=nums[i];
    }
    int cmp(const void *a, const void *b)
    {
	return *(int*)a > *(int*)b;
    }
    qsort(nums, numsSize, sizeof(int), cmp);
    int Bef=0,Aft=0,t=0;
    for(int i=0;i<numsSize;i++)
    {
        if(a[i]!=nums[i]&&t==0){
            Bef=i;
            t++;
        }
        if(a[i]!=nums[i]){
            Aft=i;
        }
    }
    return Aft-Bef+t;
}
