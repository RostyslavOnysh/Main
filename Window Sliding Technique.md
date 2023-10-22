# Window Sliding Technique : 
is a computational technique that aims to reduce the use of nested loops and replace it with a single loop, thereby reducing the time complexity.


# Problem Statement
Let us first understand the problem before going further with its approach. The problem statement is as follows, find the largest sum of K consecutive entries, given an array of size N. Not sure if you get it? Don’t worry we will understand this by taking an example.

Suppose that the following array is given to us and we are required to find 3 consecutive numbers in this array that give us the largest sum. So, k is equal to 3 in this case.

''' 
arr = [16, 12, 9, 19, 11, 8]
'''

Blocks containing three consecutive entries in the given array are [16, 12, 9], [12, 9, 19], [9, 19, 11], [19, 11, 8]. Now we calculate the sum of each block, the sum of each corresponding block is as follows: 37, 40, 39, 38. Out of all these calculated sums, the maximum sum is 40. Therefore, our output is 40.

