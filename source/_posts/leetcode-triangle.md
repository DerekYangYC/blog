title: Leetcode-Triangle
date: 2014-08-07 15:43:15
category: [leetcode]
tags: [leetcode,dp,algorithm]
---

##Triangle

###题目

Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.

For example, given the following triangle

```
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]
```

The minimum path sum from top to bottom is 11 (i.e., 2 + 3 + 5 + 1 = 11).

Note:
Bonus point if you are able to do this using only O(n) extra space, where n is the total number of rows in the triangle.


###思路

经典DP题目，与[POJ 1163](http://poj.org/problem?id=1163)几乎一样。

####第一次尝试

第一次尝试并未做对。只找出每一行的最小，然后加起来，这样的方法并不正确。像

```
[
     [2],
    [3,4],
   [6,5,2],
  [1,5,8,3]
]
```

这棵树的最小值并不是(2+3+5+5=15)，而是11。

####第二次尝试

思路改变，由上至下，遍历每一层的每个节点，计算到此节点的最小值，最后遍历最后一层，找出最小值，便是结果。

下列代码，利用一数组`tmp`存上一层的计算结果，另一数组`tmpMin`存本层的计算结果：


	public int minimumTotal(List<List<Integer>> triangle) {

		if (triangle == null || triangle.size() == 0) {
			return 0;
		}

		int[] tmpMin = new int[triangle.size()];
		// add another array to cache the previous sum value
		int[] tmp = new int[triangle.size()];

		for (int k = 0; k < triangle.size(); k++) {

			List<Integer> list = triangle.get(k);

			for (int i = 0; i < list.size(); i++) {
				if (i == 0) {
					tmpMin[i] += list.get(i);
				} else if (i == list.size() - 1) {
					tmpMin[i] = list.get(i) + tmp[i - 1];
				} else {
					tmpMin[i] = list.get(i) + Math.min(tmp[i - 1], tmp[i]);
				}
			}
			
			//let tmp became the last calculation result
			for (int i = 0; i < list.size() && k != triangle.size() - 1; i++) {
				tmp[i] = tmpMin[i];
			}

		}

		int min = tmpMin[0];
		for (Integer i : tmpMin) {
			if (i < min) {
				min = i;
			}
		}
		return min;
	}

####第一次优化

1. 由上至下需要格外处理不少边界问题，改成由下至上，则无需考虑边界问题。
2. 利用动态规划，只开一个数组存计算结果。


    public int minimumTotalWithDP(List<List<Integer>> triangle) {

		if (triangle == null || triangle.size() == 0) {
			return 0;
		}

		Integer[] min = triangle.get(triangle.size() - 1).toArray(new Integer[triangle.size()]);

		for (int i = triangle.size() - 2; i >= 0; i--) {

			for (int j = 0; j < triangle.get(i).size(); j++) {

				min[j] = Math.min(min[j], min[j + 1]) + triangle.get(i).get(j);

			}

		}

		return min[0];
    }



只是Java把`triangle`最后一层的`List<Integer>`转换为数组时，方法比较啰嗦。


####第二次优化

由于`triangle`里计算完毕的结点，原来的数据已经无用，所以其实不需要新开数组，直接利用原来的`triangle`。


	public int minimumTotalWithDP2(List<List<Integer>> triangle) {

		for (int i = triangle.size() - 2; i >= 0; i--) {

			for (int j = 0; j < triangle.get(i).size(); j++) {

				triangle.get(i).set(
						j,
						Math.min(triangle.get(i + 1).get(j), triangle.get(i + 1).get(j + 1))
								+ triangle.get(i).get(j));

			}

		}

		return triangle.get(0).get(0);
	}


参考：
[这里](http://blog.csdn.net/worldwindjp/article/details/18302041)，[这里](https://oj.leetcode.com/discuss/5337/dp-solution-for-triangle)