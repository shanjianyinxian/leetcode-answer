#### [LCP 18. 早餐组合](https://leetcode-cn.com/problems/2vYnGI/)

 可以排序解决。这里空间换时间。总共不超过x元的价格。如果首先买主食，则先统计花费不超过n元买主食总共有多少种选择（n<x）。然后针对每种饮料，查询如果买了这种饮料则剩下的钱买主食有多少种选择。最后统计结果之和。

```java
class Solution {
    public int breakfastNumber(int[] staple, int[] drinks, int x) {
        long count = 0;
        int []arr = new int[x+1];

        for (int i = 0; i < staple.length; i++) {
            int a = staple[i];

            if(a < x){
                arr[a]++;
            }
        }
        int sum = 0;
        for (int i = 1; i < arr.length; i++) {
            sum += arr[i];
            arr[i] = sum;
        }

        for (int i = 0; i < drinks.length; i++) {
            int v = x - drinks[i];
            if( v > 0){
                count += arr[v];
            }
        }

        return (int)(count % 1000000007);
    }
}
```