# 🚀 LeetCode POTD - Day 6

<table>
<tr>
<td align="left" width="400">
  <img src="https://miro.medium.com/v2/resize:fit:1100/format:webp/1*VOQU8CuPG34Gsd1yJCadOQ.png" width="100%"/>
</td>
</tr>
</table>

---

## 🧙‍♂️ 3085. Minimum Deletions to Make String K-Special

[Link to problem](https://leetcode.com/problems/minimum-deletions-to-make-string-k-special/)

---

## 🔥 Optimal Solution

```cpp
class Solution {
public:
    int minimumDeletions(string word, int k) {
        vector<int> freq(26, 0);
        
        for(char &ch : word) {
            freq[ch-'a']++;
        }
        
        int result = word.length();
        
        for(int i = 0; i < 26; i++) {
            
            int del = 0;
            
            for(int j = 0; j < 26; j++) {
                if(i == j) continue;
                
                if(freq[j] < freq[i]) {
                    del += freq[j];
                } else if(abs(freq[j] - freq[i]) > k) {
                    del += abs(freq[j] - freq[i] - k);
                }
                
            }
            
            result = min(result, del);
        }
        return result;
    }
};




