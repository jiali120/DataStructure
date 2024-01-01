# DataStructure Note From Leetcode
## Arrays and Strings
1. Arrays(1D) and strings are very similar: they both represent an ordered group of elements.
2. Similarly, strings are implemented differently between languages. In Python and Java, they are immutable. In C++, they are mutable.
   O(n), n is the size of the string if there are string ="a,b,c"
## Two Pointers
1. Two pointers is an extremely common technique used to solve array and string problems.
   
+ **One pointer in the front, and one pointer in the end**
![image](https://github.com/jiali120/DataStructure/assets/60761935/ebb30754-9573-4dee-baeb-fb2d11b35dca)

> 1. this technique will never have more than O(n) iterations for the while loop.
> 2. **Java:** Java String charAt() Method : if (s.charAt(left) != s.charAt(right)) {}; **JS:** if (s[left] != s[right]) {}; **Python:** if s[left] != s[right]:
> 3. in the two pointers example(Example 1: Given a string s, return true if it is a palindrome, false otherwise."abcdcba", or "racecar"), space is O(1) space, and the time complexity is O(n) because the while loop iterations cost O(1) each, and there can never be more than O(n) iterations of the while loop - the pointers start at a distance of n from each other and move closer by one step each iteration.

+ **Two Pointers in the front**

![image](https://github.com/jiali120/DataStructure/assets/60761935/0de25777-559e-4572-b27e-7a160498550d)

![image](https://github.com/jiali120/DataStructure/assets/60761935/05461152-4cd3-4d32-9faf-bdc737aab11f)
> 1.this method will have a linear time complexity of O(n+m) if the work inside the while loop is O(1), where n = arr1.length and m = arr2.length. This is because at every iteration, we move at least one pointer forward, and the pointers cannot be moved forward more than n + m times without the arrays being exhausted. Let's look at some examples.
> > Example 3: Given two sorted integer arrays arr1 and arr2, return a new array that combines both of them and is also sorted.

> > > ![image](https://github.com/jiali120/DataStructure/assets/60761935/149cd47e-b68a-481d-9ceb-daa576314382)
> > > this algorithm has a time complexity of O(n) and uses O(1) space
> > Example 4: 392. Is Subsequence. Given two strings s and t, return true if s is a subsequence of t, or false otherwise.A subsequence of a string is a sequence of characters that can be obtained by deleting some (or none) of the characters from the original string, while maintaining the relative order of the remaining characters. For example, "ace" is a subsequence of "abcde" while "aec" is not.
> > > this solution uses O(1) space. The time complexity is linear with the lengths of s and t.
+ Problem 344 Easy: Write a function that reverses a string. The input string is given as an array of characters s.You must do this by modifying the input array in-place with O(1) extra memory.
> > ![image](https://github.com/jiali120/DataStructure/assets/60761935/b8499c6c-fe8b-44d8-bbf3-71b187cbae6a)
> > > ![image](https://github.com/jiali120/DataStructure/assets/60761935/32ed98a5-e445-4479-8637-27702c9b30d0)
> > > ![image](https://github.com/jiali120/DataStructure/assets/60761935/af8a2346-79c1-46e1-97f4-d67a11d353f3)




## Linked Lists
### Nodes are an abstract idea. A node can be thought of as an element but with more information than just one piece of data like an integer or string.
