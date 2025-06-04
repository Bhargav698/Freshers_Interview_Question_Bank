
---

### DSA

| Q# | Question                                                                                  | Answer                                                                  | Concept(s) Tested          | Difficulty |
| -- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- | -------------------------- | ---------- |
| 1  | You need to store students' roll numbers and search quickly. Which data structure to use? | Use HashSet or HashMap for fast lookup.             | Hashing                    | Easy       |
| 2  | You are checking for balanced brackets in code editor. What approach would you use?       | Stack-based approach to match opening and closing brackets.             | Stack                      | Medium     |
| 3  | You want to implement an undo-redo feature. Which structure fits best?                    | Use two stacks: one for undo, one for redo.                             | Stack                      | Medium     |
| 4  | You're creating a leaderboard showing top scores dynamically. Which DS helps?             | Use PriorityQueue (Max Heap) to keep top scores.                        | Heap                       | Medium     |
| 5  | You want to suggest products based on typing characters. What would you use?              | Trie (Prefix Tree) for fast prefix-based searching.                     | Trie                       | Hard       |
| 6  | You want to check if two words are anagrams. What's the efficient method?                 | Count characters using an int array of size 26 (for lowercase letters). | Hashing                    | Easy       |
| 7 | You want to detect a loop in a linked list.                                               | Use Floyd’s Cycle Detection Algorithm (slow and fast pointer).          | Linked List                | Medium     |
| 8 | How would you represent a family tree with parent-child relationships?                    | Use Tree data structure, with Node having list of children.             | Tree                       | Easy       |
| 9 | Need to find shortest path in a map application. Which algo helps?                        | Use Dijkstra’s algorithm or A\* algorithm.                              | Graph, Dijkstra            | Medium     |
| 10 | Checking if a given string can be rearranged to form a palindrome.                        | Use a frequency map and check if at most one character has odd count.   | HashMap, Frequency Count   | Medium     |
| 11 | You are designing a ticket booking system where you need to manage waiting lists.         | Use Queue for FIFO management of waiting users.                         | Queue                      | Easy       |

---

### DSA Code

---

### ✅ Q1. Maximum Element in Array

```java
int maxElement(int[] arr) {
    int max = arr[0];
    for (int num : arr) {
        if (num > max) max = num;
    }
    return max;
}
```

---

### ✅ Q2. Check if String is Palindrome

```java
boolean isPalindrome(String str) {
    int i = 0, j = str.length() - 1;
    while (i < j) {
        if (str.charAt(i) != str.charAt(j)) return false;
        i++; j--;
    }
    return true;
}
```

---

### ✅ Q3. Reverse Array In-Place

```java
void reverseArray(int[] arr) {
    int i = 0, j = arr.length - 1;
    while (i < j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
        i++; j--;
    }
}
```

---

### ✅ Q4. Sum of Digits of a Number

```java
int sumOfDigits(int num) {
    int sum = 0;
    while (num > 0) {
        sum += num % 10;
        num /= 10;
    }
    return sum;
}
```

---

### ✅ Q5. Factorial of a Number

```java
int factorial(int n) {
    int fact = 1;
    for (int i = 2; i <= n; i++) {
        fact *= i;
    }
    return fact;
}
```

---

### ✅ Q6. Count Vowels and Consonants

```java
void countVowelsConsonants(String str) {
    int vowels = 0, consonants = 0;
    str = str.toLowerCase();
    for (char c : str.toCharArray()) {
        if (Character.isLetter(c)) {
            if ("aeiou".indexOf(c) != -1) vowels++;
            else consonants++;
        }
    }
    System.out.println("Vowels: " + vowels + ", Consonants: " + consonants);
}
```

---

### ✅ Q7. Second Largest in Array

```java
int secondLargest(int[] arr) {
    int first = Integer.MIN_VALUE, second = Integer.MIN_VALUE;
    for (int num : arr) {
        if (num > first) {
            second = first;
            first = num;
        } else if (num > second && num != first) {
            second = num;
        }
    }
    return second;
}
```

---

### ✅ Q8. Check If Two Strings Are Anagrams

```java
boolean isAnagram(String s1, String s2) {
    if (s1.length() != s2.length()) return false;
    int[] count = new int[26];
    for (int i = 0; i < s1.length(); i++) {
        count[s1.charAt(i) - 'a']++;
        count[s2.charAt(i) - 'a']--;
    }
    for (int c : count) {
        if (c != 0) return false;
    }
    return true;
}
```

---

### ✅ Q9. Fibonacci Series up to N Terms

```java
void printFibonacci(int n) {
    int a = 0, b = 1;
    for (int i = 0; i < n; i++) {
        System.out.print(a + " ");
        int sum = a + b;
        a = b;
        b = sum;
    }
}
```

---
Note: We can also pick easy and medium question from leetcode.