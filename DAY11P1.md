# Letter Combinations of a Phone Number
---
- ## Question:
> Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.
> 
> A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.
---
- ## Example:
> Input: digits = "23"
> 
> Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
---
- ## Solution:
**Code :**
```java
class Solution {
    public List<String> letterCombinations(String digits) {
        List<String>result=new ArrayList<>();
        if(digits.length()==0)
            return result;
        String[] letters = {"abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
        backtrack(0, letters, digits, new StringBuilder(), result);
        return result;
    }
    public void backtrack(int idx, String[] letters, String digits, StringBuilder temp, List<String> result){
    if(temp.length() == digits.length()) result.add(temp.toString()); // Step 1
    else {
        char[] letterArr = letters[digits.charAt(idx) - '2'].toCharArray(); // Step 2 & 3
        for(int j = 0; j < letterArr.length; j++){
            temp.append(letterArr[j]); // Step 4
            backtrack(idx + 1, letters, digits, temp, result); // Step 4
            temp.deleteCharAt(temp.length() - 1); // Step 5
        }
    }
}
}
