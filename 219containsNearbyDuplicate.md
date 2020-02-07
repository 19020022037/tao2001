```C
bool containsNearbyDuplicate(int* nums, int numsSize, int k){
    if(numsSize==0)
    return false;
   // if(numsSize==1)
    int mark[numsSize];//Hash表
    memset(mark,-1,sizeof(int)*numsSize);
    int i,tmp;
    for(i=0;i<numsSize;i++)
    {
        tmp=nums[i]%numsSize;//Hash函数
        if(tmp<0)//转换为正数
        tmp+=(numsSize-1);
        if(mark[tmp]==-1)//没有存数
        mark[tmp]=i;//存下数组下标
        else//已经存数
        {
            while(nums[mark[tmp]]!=nums[i])//发生冲突
            {
                tmp++;tmp%=numsSize;
                if(mark[tmp]==-1)//没有存数
                mark[tmp]=i;//存下数组下标
            }
            //已经存过该数
            if(i!=mark[tmp])
                if(i-mark[tmp]<=k)//求差值
                return true;
                else
                mark[tmp]=i;
        }
    }
    return false;
}
```
