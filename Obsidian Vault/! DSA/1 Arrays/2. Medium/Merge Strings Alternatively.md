You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return _the merged string._

**Example 1:**

**Input:** word1 = "abc", word2 = "pqr"
**Output:** "apbqcr"
**Explanation:** The merged string will be merged as so:
word1:  a   b   c
word2:    p   q   r
merged: a p b q c r

```
- initialize a result string
- while word1 < length of 1 OR word2 < length of 2, do :
- if (i < word1.length()) append word1[i] to the array
- if (i < word2.length()) append word2[i] to the array

```
