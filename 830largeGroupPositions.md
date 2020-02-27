问题描述
----------------
在一个由小写字母构成的字符串 S 中，包含由一些连续的相同字符所构成的分组。

例如，在字符串 S = "abbxxxxzyy" 中，就含有 "a", "bb", "xxxx", "z" 和 "yy" 这样的一些分组。

我们称所有包含大于或等于三个连续字符的分组为较大分组。找到每一个较大分组的起始和终止位置。

最终结果按照字典顺序输出。

示例
----------------
示例 1:

输入: "abbxxxxzzy"

输出: [[3,6]]

解释: "xxxx" 是一个起始于 3 且终止于 6 的较大分组。

示例 2:

输入: "abc"

输出: []

解释: "a","b" 和 "c" 均不是符合要求的较大分组。

示例 3:

输入: "abcdddeeeeaabbbcd"

输出: [[3,5],[6,9],[12,14]]


说明
-----------------
1 <= S.length <= 1000

C语言
--------------
```C
/**
 * Return an array of arrays of size *returnSize.
 * The sizes of the arrays are returned as *returnColumnSizes array.
 * Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
 */
int** largeGroupPositions(char * S, int* returnSize, int** returnColumnSizes){
    int n=strlen(S);
    int a[n],b[n],t=0,m=0;
    for(int i=0;i<n-1;i++)
    {
        for(int j=i+1;j<n;j++)
        {
            if(S[i]==S[j]){
                m++;
            }
            else{
                break;
            }
        }
        if(m>=2){
            a[t]=i;
            b[t]=m+1;
            t++;
        }
        i=i+m;
        m=0;
    }
    int **returnarr=(int **)malloc(sizeof(int*)*t);
    *returnColumnSizes=(int*)malloc(sizeof(int)*t);
    *returnSize=t;
    for(int i=0;i<*returnSize;i++)
    {
        (*returnColumnSizes)[i]=2;
        returnarr[i]=(int *)malloc(sizeof(int)*2);
    }
    t=0;
    for(int i=0;i<*returnSize;i++)
    {
        returnarr[i][0]=a[i];
        returnarr[i][1]=a[i]+b[i]-1;
        t++;
    }
    return returnarr;
}
