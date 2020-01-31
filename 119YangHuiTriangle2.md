C问题描述
----------------
给定一个非负索引 k，其中 k ≤ 33，返回杨辉三角的第 k 行。

示例
----------------
输入: 3

输出: [1,3,3,1]

C语言
----------------
```C
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* getRow(int rowIndex, int* returnSize){
int* a=(int *)malloc(sizeof(int)*(rowIndex+1));
unsigned long int m,sum,k,temp1,temp2,temp;     //为何要用long int型
for(int i=0;i<rowIndex+1;i++)
{
    m=i;
    k=m;
    sum=rowIndex;
    for(int j=rowIndex;j>rowIndex-i+1;j--)
    {
        sum=sum*(j-1);
        temp2=sum;
        if(k>1){
            m=m*(k-1);
            k--;
        }
        temp1=m;
        if(sum<m){
		    temp=sum;
		    sum=m;
		    m=temp;
	    }
	    while(sum%m!=0){
		   temp=sum%m;
		   sum=m;
		   m=temp;
	    }
        sum=temp2/m;
        m=temp1/m;
    }
if(m==0){
    a[i]=1;
}
else{
    a[i]=sum/m;
}
}
*returnSize=rowIndex+1;
return a;
}
