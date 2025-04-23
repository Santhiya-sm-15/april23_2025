# april23_2025
The problem that i solved today in leetcode

1.You are given an integer n.

Each number from 1 to n is grouped according to the sum of its digits.

Return the number of groups that have the largest size.

Code:
class Solution {
    public int tot(int n)
    {
        int sum=0;
        while(n>0)
        {
            sum+=n%10;
            n/=10;
        }
        return sum;
    }
    public int countLargestGroup(int n) {
        Map<Integer,Integer> m=new HashMap<>();
        int max=0;
        int sum=1;
        for(int j=1;j<=n;j++)
        {
            if(j%10==0)
                sum=tot(j);
            m.put(sum,m.getOrDefault(sum,0)+1);
            max=Math.max(max,m.get(sum));
            sum++;
        }
        int cnt=0;
        for(Map.Entry<Integer,Integer> x:m.entrySet())
        {
            if(x.getValue()==max)
                cnt++;
        }
        return cnt;
    }
}
