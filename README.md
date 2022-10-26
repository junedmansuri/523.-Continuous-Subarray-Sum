# 523.-Continuous-Subarray-Sum
Leetcode solution
class Solution {
    public boolean checkSubarraySum(int[] nums, int k) {
        Map<Integer, Integer> mp = new HashMap<>();
        int[] prefix = new int[nums.length];
        mp.put(0, -1);
        int s = 0;
        for (int i = 0; i < nums.length; ++i) {
            s += nums[i];
            int r = s % k;
            if (mp.containsKey(r) && i - mp.get(r) >= 2) {
                return true;
            }
            if (!mp.containsKey(r)) {
                mp.put(r, i);
            }
           // prefix[i]= r;
        }
        /* for(int i=0;i<nums.length;i++){
             for(int j=i+1;j<nums.length;j++){
                 if(prefix[i]==prefix[j])
                     return true;
             }
         }*/
        return false;
    }
}
