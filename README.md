# Two city scheduling
## https://leetcode.com/problems/two-city-scheduling

There are 2N people a company is planning to interview. The cost of flying the i-th person to city A is costs[i][0], and the cost of flying the i-th person to city B is costs[i][1].

Return the minimum cost to fly every person to a city such that exactly N people arrive in each city.
```
Example 1:

Input: [[10,20],[30,200],[400,50],[30,20]]
Output: 110

Explanation: 
The first person goes to city A for a cost of 10.
The second person goes to city A for a cost of 30.
The third person goes to city B for a cost of 50.
The fourth person goes to city B for a cost of 20.
```
The total minimum cost is 10 + 30 + 50 + 20 = 110 to have half the people interviewing in each city.
 

**Note:**

1. 1 <= costs.length <= 100
2. It is guaranteed that costs.length is even.
3. 1 <= costs[i][0], costs[i][1] <= 1000

# Implementation :
```java
class Solution {
  public int twoCitySchedCost(int[][] costs) {
    // Sort by a gain which company has 
    // by sending a person to city A and not to city B
    Arrays.sort(costs, new Comparator<int[]>() {
      public int compare(int[] c1, int[] c2) {
        return (c1[0] - c1[1]) - (c2[0] - c2[1]);
      }
    });

    int total = 0;
    // To optimize the company expenses,
    // send the first n persons to the city A and the others to the city B
    for (int i = 0; i < costs.length; i++) {
        if(i < costs.length / 2)
            total += costs[i][0];
        else 
            total += costs[i][1];
    } 
    return total;
  }
}
```

# References :
1. https://www.youtube.com/watch?v=8Gm0jxpRBGw
2. https://leetcode.com/articles/two-city-scheduling
