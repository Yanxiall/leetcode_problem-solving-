# Question Description:

#### The greatest value of gifts

1. There is a gift in each grid of an m * n chess board, and each gift has a certain value (value greater than 0). You can take the gift in the grid from the upper left corner of the board and move one grid each time to the right or down until you reach the lower right corner of the board. Given the value of a chess board and the gifts on it, please calculate how much value of the gifts you can get at most?

   **Example 1:**  

   Input:  
   [  
     [1,3,1],  
     [1,5,1],  
     [4,2,1]  
   ]   
   Output: 12   
   **Explanation:**  
   Through the path 1->3->5->2->1 get the gifts with the most value    

# Idea:

**Dynamic Programming:**

Define a twp dimensions vector dp, of which  dp[i] [j] means that you can get the most value of the gift at grid[i] [j]. Because every time we can only move one block from upper left to the right or down, so:   

`dp[i] [j] = max(dp[i-1] [j], dp[i] [j-1]) + grid [i] [j].`  

# Solution:

**C++:**

`class Solution {`

`public:`

  `int maxValue(vector<vector<int>>& grid) {`

​    `if(grid.empty()) return 0;`

​    `int m = grid.size();`

​    `int n = grid[0].size();`

​    `vector<vector<int>> dp(m,vector<int>(n,0));`

​    `dp[0][0] = grid[0][0];`

​    `for(int i = 0; i < m; i++)`

​    `{`

​      `for(int j = 0; j < n; j++)`

​      `{`

​        `if(i >=1 && j >= 1)` 

​         `dp[i][j] = grid[i][j] + max(dp[i-1][j],dp[i][j-1]);`

​        `else if(i <1 && j >= 1)`

​         `dp[i][j] = dp[i][j-1] + grid[i][j];`

​        `else if(i >= 1 && j < 1)`

​         `dp[i][j] = dp[i-1][j] + grid[i][j];`  

​      `}`

​    `}`

​    `return dp[m-1][n-1];`

  `}`

`};`