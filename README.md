# DataStructure Note From Leetcode
## Arrays and Strings
1. Arrays(1D) and strings are very similar: they both represent an ordered group of elements.
2. Similarly, strings are implemented differently between languages. In Python and Java, they are immutable. In C++, they are mutable.
   O(n), n is the size of the string if there are string ="a,b,c"
### Two Pointers
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

### Sliding Window
1. Like two pointers, sliding windows work the same with arrays and strings - the important thing is that they're iterables with ordered elements.

**When should we use sliding window?**

> There is a very common group of problems involving subarrays that can be solved efficiently with sliding window. Let's talk about how to identify these problems.

+ First, the problem will either explicitly or implicitly define criteria that make a subarray "valid". There are 2 components regarding what makes a subarray valid:

> 1. A constraint metric. This is some attribute of a subarray. It could be the sum, the number of unique elements, the frequency of a specific element, or any other attribute.
> 2. A numeric restriction on the constraint metric. This is what the constraint metric should be for a subarray to be considered valid.
> > For example, let's say a problem declares a subarray is valid if it has a sum less than or equal to 10. The constraint metric here is the sum of the subarray, and the numeric restriction is <= 10. A subarray is considered valid if its constraint metric conforms to the numeric restriction, i.e. the sum is less than or equal to 10.

+ Second, the problem will ask you to find valid subarrays in some way.

> 1. The most common task you will see is finding the best valid subarray. The problem will define what makes a subarray better than another. For example, a problem might ask you to find the longest valid subarray.
> 2. Another common task is finding the number of valid subarrays. We will take a look at this later in the article.
> > Whenever a problem description talks about subarrays, you should figure out if sliding window is a good option by analyzing the problem description. If you can find the things mentioned above, then it's a good bet.

> 3. Implementation
+ When we add a new element from the right, we just do curr += nums[right]. When we remove an element from the left, we just do curr -= nums[left]. This way, all operations are done in O(1).
+ use for loop move the right pointer
+ use while(curr>k){left++} to move left pointer
+ Finally, how do we update the answer? In each for loop iteration, after the while loop, the current window is valid. We can write code here to update the answer. The formula for the length of a window is right - left + 1.
  ![image](https://github.com/jiali120/DataStructure/assets/60761935/74301c97-c6e4-4ed2-a60b-c073468ba431)
  ![image](https://github.com/jiali120/DataStructure/assets/60761935/fdc806dd-afd9-4f86-9e90-84f9fecff901)

![image](https://github.com/jiali120/DataStructure/assets/60761935/802ff8ae-4555-46dc-b046-3c2e3d5710c2)
![image](https://github.com/jiali120/DataStructure/assets/60761935/91d41550-6369-4eac-831f-cdb06058cdb0)
> this algorithm has a time complexity of O(n) since all work done inside the for loop is amortized O(1), where n is the length of nums. The space complexity is constant because we are only using 3 integer variables.

+ Example 2: You are given a binary string s (a string containing only "0" and "1"). You may choose up to one "0" and flip it to a "1". What is the length of the longest substring achievable that contains only "1"? For example, given s = "1101100111", the answer is 5. If you perform the flip at index 2, the string becomes 1111100111.
  > Because the string can only contain "1" and "0", another way to look at this problem is "what is the longest substring that contains at most one "0"?". This makes it easy for us to solve with a sliding window where our condition is window.count("0") <= 1. We can use an integer curr that keeps track of how many "0" we currently have in our window.
  > ![image](https://github.com/jiali120/DataStructure/assets/60761935/d06dbbc8-e4a0-4d18-bab5-2cd8654d1eaf)

+ Number of subarrays
> If a problem asks for the number of subarrays that fit some constraint, we can still use sliding window, but we need to use a neat math trick to calculate the number of subarrays.

> Let's say that we are using the sliding window algorithm we have learned and currently have a window (left, right). How many valid windows end at index right?

> There's the current window (left, right), then (left + 1, right), (left + 2, right), and so on until (right, right) (only the element at right).
> You can fix the right bound and then choose any value between left and right inclusive for the left bound. Therefore, the number of valid windows ending at index right is equal to the size of the window, which we know is right - left + 1.
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/d23abf40-eacc-483b-88c8-4ab567a8fb80)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/244c1ae6-4c59-4dbd-b75b-b63bd3a43454)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/00e2eaba-7461-4df6-9edf-89de3922a703)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/0a273d29-a377-4b35-96bc-afa9909e7852)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/f2c2d689-d24f-40bc-8806-20438998330d)

+ Example 4: Given an integer array nums and an integer k, find the sum of the subarray with the largest sum whose length is k.

> As we mentioned before, we can build a window of length k and then slide it along the array. Add and remove one element at a time to make sure the window stays size k. If we are adding the value at i, then we need to remove the value at i - k.

> After we build the first window we initialize our answer to curr to consider the first window's sum.
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/17875916-bf88-49eb-9e3b-b05b1e721e82)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/f67aba89-49c5-47a5-9816-4265c3184ffe)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/7930cd4d-2c51-4619-926e-95876065f512)

![image](https://github.com/jiali120/DataStructure/assets/60761935/7437dfc4-b5a8-4eda-a372-2133449fec77)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/f301af40-da8c-4f8b-8126-c300c3e3a9e1)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/905ca197-c28e-4450-8f7f-e22aa025546f)
> > ![image](https://github.com/jiali120/DataStructure/assets/60761935/6ff61653-bdfd-4b75-a54a-87201a031fe7)
> > ![image](https://github.com/jiali120/DataStructure/assets/60761935/ebcabce1-def6-4fab-8645-48dc0c66c156)
> > ![image](https://github.com/jiali120/DataStructure/assets/60761935/a12f3a0d-a65c-4f85-9c18-3db5776e468f)
> > ![image](https://github.com/jiali120/DataStructure/assets/60761935/2b69406c-24a2-4090-8ee2-3f4cf57811cb)
> > ![image](https://github.com/jiali120/DataStructure/assets/60761935/0df148b8-3b4f-4efd-9bf0-4c4edba8542f)



## Linked Lists
### Nodes are an abstract idea. A node can be thought of as an element but with more information than just one piece of data like an integer or string.
**advantage:**
1. you can add and remove elements at any position in O(1).
2. linked lists have the advantage of not having fixed sizes.While dynamic arrays can be resized, under the hood they still are allocated a fixed size - it's just that when this size is exceeded, the array is resized, which is expensive.
**disadvantages:**
1. linked lists have more overhead than arrays - every element needs to have extra storage for the pointers. If you are only storing small items like booleans or characters, then you may be more than doubling the space needed.




## Networking is a playground for interdisciplinary research innovations
The Internet's huge transformative role is connected with an ever-expanding and evolving collection of technologies, system and protocol architectures, algorithms, as well as powerful applications. Indeed, the Internet is an amazing “playground” of ongoing cross-disciplinary innovations. These innovations are coming from fields such as distributed systems, operating systems, computer architecture, software engineering, algorithms and data structures, graph theory, queuing theory, and game theory, to name a few. Additionally, these include mechanism designs stemming from machine learning and AI, cryptography, programming languages, formal methods, and more. 
