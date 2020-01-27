给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。
'[int maxSubArray(int* nums, int numsSize){
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
}]'
