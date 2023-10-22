# Window Sliding Technique : 
is a computational technique that aims to reduce the use of nested loops and replace it with a single loop, thereby reducing the time complexity.


# Problem Statement
Let us first understand the problem before going further with its approach. The problem statement is as follows, find the largest sum of K consecutive entries, given an array of size N. Not sure if you get it? Don’t worry we will understand this by taking an example.

Suppose that the following array is given to us and we are required to find 3 consecutive numbers in this array that give us the largest sum. So, k is equal to 3 in this case.

arr = [16, 12, 9, 19, 11, 8]

Blocks containing three consecutive entries in the given array are [16, 12, 9], [12, 9, 19], [9, 19, 11], [19, 11, 8]. Now we calculate the sum of each block, the sum of each corresponding block is as follows: 37, 40, 39, 38. Out of all these calculated sums, the maximum sum is 40. Therefore, our output is 40.


# Naive Approach
There exists an inefficient but simple approach to solving this problem. You may be wondering why are we discussing this approach when it is not efficient enough. Well, one must know the importance of a good approach, right? Also, understanding this approach allows us to build upon the knowledge to allows us to develop a more efficient algorithm called the sliding window algorithm.

In this approach, we begin with the first index and add up until the kth element is reached. For all possible consecutive blocks or groups of k elements, we repeat the process. This approach uses a nested for loop; the outer for loop begins with the first element of the k-element block, and the inner or nested loop continues until the kth element is reached.

As this approach contains two nested loops, therefore, the complexity of this approach is O(N*K). Where n is the size of the array given to us and k is the number of consecutive subentries to be considered. Now what we tell you that this task can be achieved in much less time, can’t believe it? Look for yourself below.

# What is the Sliding Window Algorithm?
The Sliding Window algorithm is a method for finding a subset of elements that satisfy a certain condition in issues. Maintaining a window containing elements from an array or string while advancing the window in a particular direction until the required subset is found is how this method operates.

The fundamental concept is to define the window using two pointers, a left pointer, plus a right pointer. Beginning with the first element of the array or string, both pointers are set to the same value. Then, after moving the right pointer to locate the desired subset, we push the left pointer to enlarge the window until we are no longer able to improve the outcome.

Until the full array or string has been evaluated, this procedure is repeated. When trying to select a subset of elements that satisfy a certain requirement, the sliding window approach comes in handy. The Sliding Window algorithm, for instance, can be used to identify the longest substring, the shortest substring, or the substring with the largest or minimum sum.

Another instance is when we have to determine the highest or lowest sum of a subarray with size k fixed. The Sliding Window technique can be used in this situation to keep a window of k items and slide the window around until that we locate the subset containing the desired sum.

# Full Algorithm
Here are the steps for applying the sliding window algorithm:

Add the first K components together and save the result in the currentSum variable. Because this is the first sum, it is also the current maximum; thus, save it in the variable maximumSum.
As the window size is K, we move the window one place to the right and compute the sum of the items in the window.
Update the maximum if the currentSum is greater than the maximumSum, and repeat step 2.



# Here is the code to implement Sliding Window Algorithm in Java:
''' java 
public class slidingwindow {

    static int maxSum(int[] arr,int k){
        //length of the array
        int n=arr.length;

        //length of array(n) must be greater than window size(k)
        if(n<k){
            System.out.println("Invalid");
            return -1;
        }

        //sum of first k(window size) elements
        int window_sum=0;
        for(int i=0;i<k;i++) window_sum+=arr[i];

        int max_sum=window_sum;

        //Calculating sums of remaining windows by
        //removing first element of previous window
        //and adding last element of current window
        //this way our window moves forward.

        //Also updating the maximum sum to current window sum
        // if the current window sum is greater
        // than existing maximum sum.
        for(int i=k;i<n;i++){
            window_sum+=(arr[i]-arr[i-k]);
            max_sum=Math.max(window_sum,max_sum);
        }

        return max_sum;
    }

    public static void main(String[] args) {
        //window size
        int k=3;
        int[] arr={16, 12, 9, 19, 11, 8};
        System.out.println(maxSum(arr,k));
    }


}
'''
