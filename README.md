# Sort-character-by-frequency


## Problem Statement

Given a string `s`, sort it in decreasing order based on the frequency of the characters. The frequency of a character is the number of times it appears in the string. Return the sorted string. If there are multiple answers, return any of them.

### Examples

**Example 1:**

- **Input:** `s = "tree"`
- **Output:** `"eert"`
- **Explanation:** 'e' appears twice while 'r' and 't' both appear once. So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.

**Example 2:**

- **Input:** `s = "cccaaa"`
- **Output:** `"aaaccc"`
- **Explanation:** Both 'c' and 'a' appear three times, so both "cccaaa" and "aaaccc" are valid answers. Note that "cacaca" is incorrect, as the same characters must be together.

**Example 3:**

- **Input:** `s = "Aabb"`
- **Output:** `"bbAa"`
- **Explanation:** "bbaA" is also a valid answer, but "Aabb" is incorrect. Note that 'A' and 'a' are treated as two different characters.

### Constraints

- \(1 \leq s.length \leq 5 \times 10^5\)
- `s` consists of uppercase and lowercase English letters and digits.

## Solution

Below is the Swift solution to the problem, which sorts the string based on character frequency:

```swift
func frequencySort(_ s: String) -> String {
    // Initialize an empty string for the result
    var str = ""

    // Dictionary to count the frequency of each character
    var dict: [Character: Int] = [:]

    // Count the frequency of each character in the input string
    for item in s {
        if let count = dict[item] {
            dict[item] = count + 1
        } else {
            dict[item] = 1
        }
    }

    // Sort the dictionary by frequency in descending order
    let sorted = dict.sorted {
        return $0.value > $1.value
    }

    // Construct the result string based on sorted characters
    for (key, value) in sorted {
        for _ in 0..<value {
            str += String(key)
        }
    }
    
    return str
}

// Example usage
let input = "tree"
let output = frequencySort(input)
print("Sorted string by frequency: \(output)")
// Output: "eert" or "eetr"

