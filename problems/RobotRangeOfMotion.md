# Question Description:

**13.Robot's range of motion**

There is a grid with m rows and n columns on the ground, from coordinate[0,0] to coordinate[m-1,n-1]. A robot begins to move from the coordinate [0,0]. But it can only move for one grid to left, right, up and down at a time(It can not move outside the grid) and is not allowed into the grid the sum of digits of the coordinate of which is greater than k. For example, when k is 18, the robot is allowed into the grid[35,37], because 3 + 5 + 3 + 7 = 18, but it can not enter the grid[35, 38], because 3 + 5 +3 + 8 = 19 > 18.  How many grids can the  robot enter?  

# Idea:

**BFS:**

A queue is defined to achieve BFS, through push and pop we can traverse the grid downwards and right. A vector which has the same size as the grid is defined to store the coordinate which has been traversed. In this way we can avoid the repeating and reduce the amount of the comuptation.  While traversing we judge each grid and count the grid which meet the requirement.   

# Solution:

**C++:**

`class Solution {`

`public:`

  `int movingCount(int m, int n, int k) {` 

   `if(!k) return 1;`    

   `queue<pair<int, int>> q;`

   `int dx[2] = {0,1};`

   `int dy[2] = {1,0};`

   `vector<vector<int>> vis(m, vector<int>(n,0));`

   `vis[0][0] = 1;` 

   `int res = 1;`    

   `q.push(make_pair(0,0));`

   `while(!q.empty())`

   `{`

​    `auto [x,y] = q.front();`

​    `q.pop();`

​    `for(int i = 0; i < 2; i++)`

​    `{`

​      `int tx = x + dx[i];`

​      `int ty = y + dy[i];`

​      `if(tx < 0 ||ty < 0 || tx >= m || ty >= n || (Addindex(tx) + Addindex(ty)) > k || vis[tx][ty] == 1)  continue;`

​      `q.push(make_pair(tx,ty));`

​      `vis[tx][ty] = 1;`

​      `res++;`    

​      `}`     

​    `}`

​    `return res;` 

  `}`

  `int Addindex(int i)`

  `{`

   `int sum = 0;`

   `while(i != 0)`

   `{`

​    `sum += i % 10;`

​    `i = i / 10;`     

   `}`    

   `return sum;`

  `}`    

`};`

