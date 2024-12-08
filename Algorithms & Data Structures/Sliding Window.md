This technique helps efficiently find substrings with unique characters by using two indices that define a **window** within the string. The indices are used to track the start and the end of the current substring, ensuring that all characters within this window are unique.

- **`i`**: This is the starting index of the window. It tracks the start of the substring we are currently evaluating.
- **`j`**: This is the current index in the string. It expands the window as we iterate through the characters.

The goal of the sliding window is to **expand** the window as long as the substring contains unique characters. When a **repeating character** is found, the window is "shifted" forward by adjusting `i`, which removes the previous occurrence of the repeating character and allows the substring to stay unique.

fun lengthOfLongestSubstring(s: String): Int {  
    var result = 0  
    val charsMap = mutableMapOf<Char, Int>()  
    var i = 0  
  
    for (j in s.indices) {  
        if (charsMap.containsKey(s[j])) {  
            i = maxOf(charsMap[s[j]]!! + 1, i)  
        }  
        charsMap[s[j]] = j  
        result = maxOf(result, j - i + 1)  
    }  
  
    return result  
}