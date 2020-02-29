问题描述
--------------
3 x 3 的幻方是一个填充有从 1 到 9 的不同数字的 3 x 3 矩阵，其中每行，每列以及两条对角线上的各数之和都相等。

给定一个由整数组成的 grid，其中有多少个 3 × 3 的 “幻方” 子矩阵？（每个子矩阵都是连续的）。

示例
----------------
示例：

输入: 

[[4,3,8,4],

[9,5,1,9],

[2,7,6,2]]

输出: 1

解释: 

下面的子矩阵是一个 3 x 3 的幻方：

438

951

276

而这一个不是：

384

519

762

总的来说，在本示例所给定的矩阵中只有一个 3 x 3 的幻方子矩阵。

提示:
----------------
1 <= grid.length <= 10
	
1 <= grid[0].length <= 10

0 <= grid[i][j] <= 15

C语言
-----------------
```C
int numMagicSquaresInside(int** grid, int gridSize, int* gridColSize){
    int /*rd=grid[gridColSize-2][*gridColSize-2],*/std=0,t=0;
    for(int i=1;i<gridSize-1;i++)
    for(int j=1;j<*gridColSize-1;j++)
    {
        if(!(grid[i-1][j-1]+grid[i-1][j]+grid[i-1][j+1]+grid[i][j-1]+grid[i][j]+grid[i][j+1]+grid[i+1][j-1]+grid[i+1][j]+grid[i+1][j+1]==45&&grid[i-1][j-1]*grid[i-1][j]*grid[i-1][j+1]*grid[i][j-1]*grid[i][j]*grid[i][j+1]*grid[i+1][j-1]*grid[i+1][j]*grid[i+1][j+1]==1*2*3*4*5*6*7*8*9)){
            continue;
        }
        std=grid[i-1][j-1]+grid[i-1][j]+grid[i-1][j+1];
        if(grid[i-1][j-1]+grid[i][j-1]+grid[i+1][j-1]==std&&grid[i-1][j]+grid[i][j]+grid[i+1][j]==std&&grid[i-1][j+1]+grid[i][j+1]+grid[i+1][j+1]==std&&grid[i][j-1]+grid[i][j]+grid[i][j+1]==std&&grid[i+1][j-1]+grid[i+1][j]+grid[i+1][j+1]==std&&grid[i-1][j-1]+grid[i][j]+grid[i+1][j+1]==std&&grid[i-1][j+1]+grid[i][j]+grid[i+1][j-1]==std){
            t++;
        }
    }
    return t;
}
