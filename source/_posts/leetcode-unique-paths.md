title: Leetcode-Unique Paths
date: 2014-08-07 17:56:24
category: [leetcode]
tags: [leetcode,dp,algorithm]
---

##Unique Paths 

###题目

A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

![](/img/robot_maze.png)

Above is a 3 x 7 grid. How many possible unique paths are there?

Note: m and n will be at most 100.

###思路

此题与`Project Euler`的[第15题](http://projecteuler.net/problem=15)类似。

题目可以抽象为在坐标的第四象限，从原点(0,0)走到(m-1,n-1)有多少种方法。

关键的思路在于，发现`到(x,y)的走法数=到(x-1,y)的走法数+到(x,y-1)的走法数`，如下图

![](/img/lattice_paths_4.png)

找到这个关键的递推公式后，无论是利用递归还是动态规划，都能解决问题：

	//Use dp
	public int uniquePaths(int m, int n) {

		if (m <= 0 || n <= 0) {
			return 0;
		}

		int[][] paths = new int[m][n];

		for (int i = 0; i < m; i++) {
			for (int j = 0; j < n; j++) {

				if (i == 0 || j == 0) {
					paths[i][j] = 1;
				} else {
					paths[i][j] = paths[i - 1][j] + paths[i][j - 1];
				}

			}
		}

		return paths[m - 1][n - 1];
	}


	//Use Recursion
	public int uniquePaths2(int m, int n) {

		if (m <= 0 || n <= 0)
			return 0;

		return cal(m - 1, n - 1);

	}
	public int cal(int i, int j) {
		if (i == 0 || j == 0) {
			return 1;
		} else {
			return cal(i - 1, j) + cal(i, j - 1);
		}
	}


第一次遇到这题是一次（失败的）面试。面试官开口第一道题便是这题。当时不知道是脑袋浆糊了还是过于紧张，反正没答出来。

之后看过[一个解法](http://oldj.net/article/lattice-paths/)后就明白了。还有一个更加直观的思路，在坐标系中，只能向右或者向上走，从原点到坐标(m,n)，无论怎么走，向右都得走m步，向上都得走n步，才能到达(m,n)。所以的话，总共不同的走法数是，$(m+n)\choose m$