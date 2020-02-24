```C
int minCostClimbingStairs(int* cost, int costSize){
    int a =0;
    int b =0;
    int c;
    for(int i = costSize-1;i>-1;i--)
    {
        c = cost[i]+fmin(a,b);
        b =a;
        a =c;
    }
    return fmin(a,b);
}
