问题描述
-----------------
给定 n 个整数，找出平均数最大且长度为 k 的连续子数组，并输出该最大平均数。

示例
----------
示例 1:

输入: [1,12,-5,-6,50,3], k = 4

输出: 12.75

解释: 最大平均数 (12-5-6+50)/4 = 51/4 = 12.75

注意:
-----------------------

	1 <= k <= n <= 30,000。
	
  所给数据范围 [-10,000，10,000]。

C语言
--------------
```C
double findMaxAverage(int* nums, int numsSize, int k){
    int sum=0;
    double max=0;
    for(int i=0;i<k;i++)
    {
        sum+=nums[i];
    }
    max=sum;
    for(int i=0;i<numsSize-k;i++)
    {
        sum=sum+nums[i+k]-nums[i];
        if(max<sum){
            max=sum;
        }
    }
    return max/k;
}
