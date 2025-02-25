# Leetcode-1524

# C++

class Solution {
public:
    int numOfSubarrays(vector<int>& arr) {
        int even=0,odd=0;
        long long ans=0;
        for(int i=0;i<arr.size();i++)
        {
            if(i>0)
            {
                arr[i]=arr[i]+arr[i-1];
            }
            if(arr[i]&1)odd++;
            else
            even++;
        }
        ans=odd;
        ans%=(1000000007);
        for(int i=0;i<arr.size();i++)
        {
            if(arr[i]&1)
            {
                odd--;
                ans+=even;
            }
            else
            {
                even--;
                ans+=odd;
            }
            ans%=(1000000007);
        }
        return ans;
    }
};

# Python

class Solution:
    def numOfSubarrays(self, arr):
        even, odd = 0, 0
        ans = 0
        MOD = 1000000007

        # Prefix sum logic
        for i in range(len(arr)):
            if i > 0:
                arr[i] += arr[i - 1]
            if arr[i] % 2 == 1:
                odd += 1
            else:
                even += 1

        ans = odd % MOD

        # Counting subarrays based on prefix sum parity
        for i in range(len(arr)):
            if arr[i] % 2 == 1:
                odd -= 1
                ans += even
            else:
                even -= 1
                ans += odd
            ans %= MOD

        return ans

# Java

class Solution {
    public int numOfSubarrays(int[] arr) {
        int even = 0, odd = 0;
        long ans = 0;
        final int MOD = 1000000007;

        // Prefix sum logic
        for (int i = 0; i < arr.length; i++) {
            if (i > 0) {
                arr[i] += arr[i - 1];
            }
            if (arr[i] % 2 == 1) {
                odd++;
            } else {
                even++;
            }
        }

        ans = odd % MOD;

        // Counting subarrays based on prefix sum parity
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] % 2 == 1) {
                odd--;
                ans += even;
            } else {
                even--;
                ans += odd;
            }
            ans %= MOD;
        }

        return (int) ans;
    }
}
