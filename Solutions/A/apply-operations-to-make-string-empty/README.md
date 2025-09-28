# Apply operations to make string empty

[Problem link](https://leetcode.com/problems/apply-operations-to-make-string-empty/)

## Solutions


### Solution.py
```py
# https://leetcode.com/problems/apply-operations-to-make-string-empty/

class Solution:
    def lastNonEmptyString(self, s: str) -> str:
        ctr = Counter(s)
        maxct = max(ctr.values())

        last = {}
        for i, x in enumerate(s):
            last[x] = i
        return ''.join(sorted(
            [c for c, v in ctr.items() if v == maxct],
            key=lambda x: last[x]
        ))
```
## Tags

* [Hashmap](/Collections/hashmap.md#hashmap) > [Counter](/Collections/hashmap.md#counter)
* [Array scanning](/Collections/array-scanning.md#array-scanning)


### Comments

#### Question:
At each operation, the first occurence of every alphabet is removed. Return the value of the string s right before applying the last operation. 

#### Answer:
Create a character frequency counter
Iterate over the string in reverse to gather only the last occuring value character
Add character to answer string if it has the maximum frequency (part of the remaining set) and not already added to the answer string.
Reverse the answer string and return.

