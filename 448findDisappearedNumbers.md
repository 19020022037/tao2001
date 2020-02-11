/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* findDisappearedNumbers(int* nums, int numsSize, int* returnSize){
    for(int i=0;i<numsSize;i++) 
    { 
        if(nums[i]!=i+1) {
            int m,j=nums[i]; 
            while(1) { 
                if(nums[j-1]==j) 
                break; 
                m=nums[j-1]; 
                nums[j-1]=j; 
                j=m; 
            } 
        }
}
int k=0; 
int *N=(int*)malloc(1*sizeof(int)); 
for(int j=0;j<numsSize;j++) 
{ 
    if(nums[j]!=j+1) {
        if(k==0) 
        N[k++]=j+1; 
    else { 
        N=(int*)realloc(N,(k+1)*sizeof(int)); 
        N[k++]=j+1; 
    } 
    } 
    } 
    *returnSize=k; 
    return N; 
}
