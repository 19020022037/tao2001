问题描述
------------------
给你一个整数数组 arr ，请你将数组中的每个元素替换为它们排序后的序号。

序号代表了一个元素有多大。序号编号的规则如下：

序号从 1 开始编号。

一个元素越大，那么序号越大。如果两个元素相等，那么它们的序号相同。

每个数字的序号都应该尽可能地小。

示例
----------------
示例 1：

输入：arr = [40,10,20,30]

输出：[4,1,2,3]

解释：40 是最大的元素。 10 是最小的元素。 20 是第二小的数字。 30 是第三小的数字。

示例 2：

输入：arr = [100,100,100]

输出：[1,1,1]

解释：所有元素有相同的序号。

示例 3：

输入：arr = [37,12,28,9,100,56,80,5,12]

输出：[5,3,4,2,8,6,7,1,3]

提示：
-------------------
0 <= arr.length <= 10的5次方

-10的9次方 <= arr[i] <= 10的9次方

C语言
-----------------
```C
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* arrayRankTransform(int* arr, int arrSize, int* returnSize){
    /*int *a=(int *)malloc(sizeof(int)*arrSize);
    int *b=(int *)malloc(sizeof(int)*arrSize);
    for(int i=0;i<arrSize;i++)
    {
        a[i]=arr[i];
    }
    int cmp(const void *a, const void *b)
    {
	return *(int*)a > *(int*)b;
    }
    qsort(a, arrSize, sizeof(int), cmp);
    int t=1,m=0;
    for(int i=0;i<arrSize;i++)
    {
        for(int j=0;j<arrSize;j++)
        {
            if(a[i]==arr[j]){
                b[j]=t;
                m++;
            }
        }
        if(m>1){
            i=i+m-1;
        }
        m=0;
        t++;
    }
    return b;*/
    struct Cool{
        int num;
        int af;
        int Be;
    };
    struct Cool *a=(struct Cool *)malloc(sizeof(struct Cool)*arrSize);
    for(int i=0;i<arrSize;i++)
    {
        a[i].Be=i;
        a[i].num=arr[i];
    }
    int cmp1(const void *p,const void *q)
    {
        int c= ((struct Cool*)p)->num - ((struct Cool*)q)->num;
        if(c>0) 
            return 1;
        else 
            return -1;
    }
    qsort(a, arrSize, sizeof(struct Cool), cmp1);
    int t=1;
    for(int i=0;i<arrSize-1;i++)
    {
        if(a[i].num==a[i+1].num){
            a[i].af=t;
            a[i+1].af=t;
        }
        else{
            a[i].af=t;
            t++;
            a[i+1].af=t;
        }
    }
    int cmp2(const void *p,const void *q)
    {
        int c= ((struct Cool*)p)->Be - ((struct Cool*)q)->Be;
        if(c>0) 
            return 1;
        else 
            return -1;
    }
    qsort(a, arrSize, sizeof(struct Cool), cmp2);
    int *b=(int *)malloc(sizeof(int)*arrSize);
    *returnSize=arrSize;
    for(int i=0;i<arrSize;i++)
    {
        b[i]=a[i].af;
    }
    if(arrSize==1){
        b[0]=1;
        return b;
    }
    return b;
}
