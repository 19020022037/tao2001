问题描述
------------
给定一个由整数组成的非空数组所表示的非负整数，在该数的基础上加一。
最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。
你可以假设除了整数 0 之外，这个整数不会以零开头。

示例
-----------
示例【1】  
输入: [1,2,3]  
输出: [1,2,4]  
解释: 输入数组表示数字 123。  
示例【2】  
输入: [4,3,2,1]  
输出: [4,3,2,2]  
解释: 输入数组表示数字 4321。  

C语言
----------
```C
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* plusOne(int* digits, int digitsSize, int* returnSize){
    int *a=(int *)malloc(digitsSize*sizeof(int)+sizeof(int));
    digits[digitsSize-1]=digits[digitsSize-1]+1;
    int i=digitsSize-1;
    while(i>=1){
        if(digits[i]==10){
            digits[i-1]=digits[i-1]+1;
            digits[i]=0;
        }
        i--;
    }
    if(digits[0]==10){
        a[0]=1;
        for(int j=1;j<digitsSize+1;j++){
            a[j]=0;
        }
        *returnSize=digitsSize+1;
        return a;
    }
    *returnSize=digitsSize;
    return digits;
}
```
