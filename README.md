# Algorithms for Problem Solving
This is what I organized through solving various problems that require some complicated algorithms. 

### Contents

[1. Largest Sum Contiguous Subarray](#largest-sum-algorithm)

[2. Binary Search](#binary-search-algorithm)



## Largest Sum Algorithm

   This is used to find the sum of the subarray that has the maximum sum. For example, if there is an array of 5 integers, [-1, -2, 3, 1, -8], the subarray with the largest sum would be [3, 1]. 

   We could use two for loops to grab every sum of every subarray, but this very inefficient if the size of the array is big. So, we use Kandane's algorithm to find the subarray with maximum sum. [More](https://www.geeksforgeeks.org/largest-sum-contiguous-subarray/) This is very efficient and easy to use. Before the code, there is one more concept, which is the prefix sum. 

### Prefix Sum Algorithm

   So, if there is an array a [1 2 3 4 5] and we want to find the sum of the second element until the fourth element, which is 2+3+4 = 9, we can go through for loops. However, there is a better way. If we cumulate the sum and write a[3] - a[0], it will give you exactly 9. [More](https://en.wikipedia.org/wiki/Prefix_sum)
    
```

- input: 
5 -> size of the input array
2 1 -2 3 -5 -> array

- output:
4 -> [2 1 -2 3]

#include <cstdio>
#include <algorithm>

using namespace std;

int m;
int a[1005] = {0,};

int main() {
    scanf("%d", &m);
    for(int i = 1; i <= m; i++) {
        int x;
        scanf("%d", &x);
        a[i] = a[i-1] + x; //prefix sum
    }
  
    int sum1, sum2 = 0;
    int ret = -1005;
    for(int i = 1; i <= m; i++) {
        sum1 = a[i];
        ret = max(sum1 - sum2, ret);
        sum2 = min(sum2, sum1);
    }
    printf("%d", ret);
}
```


## Binary Search Algorithm

   This is used to find an element in an array which is much more effiecent than linear search, which is basically going through every elements. The array has to be initially sorted in order to go through the binary search algorithm. [More](https://www.geeksforgeeks.org/binary-search/)

```
- output: 3

#include <cstdio>
#include <algorithm>

using namespace std;

int binarySearch(int x, int array[]) {
    
    int l,m = 0;
    int h = sizeof(array) - 1;
    
    while(l<=h){
        m = (l+h)/2;
        if(x<array[m]) h=m-1;
        else if(x>array[m]) l=m+1;
        else return m;
    }
    return -1;
}

int main() {
    
    int array[] = {1, 2, 3, 4, 5}; //array has to be sorted before using binary search
    sort(array, array+5);
    printf("%d", binarySearch(4, array));
}
```









