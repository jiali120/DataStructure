# DataStructure Note From Leetcode
## Arrays and Strings
1. Arrays(1D) and strings are very similar: they both represent an ordered group of elements.
2. Similarly, strings are implemented differently between languages. In Python and Java, they are immutable. In C++, they are mutable.
   O(n), n is the size of the string if there are string ="a,b,c"

### Prefix Sum
+ 560. Subarray Sum Equals K
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/9aa9beab-2522-48b1-99a6-8a1c09c7aeb6)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/6b68a26d-5e2d-4738-b54b-16327bafc9d1)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/171aa9a4-87f5-40bd-a322-4f6a8b94d2d8)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/5624912a-3ce2-4983-81a9-83aafc7e6fcc)
+ To summarize:
> + We use curr to track the prefix sum.
> + At any index i, the sum up to i is curr. If there is an index j whose prefix is curr - k, then the sum of the subarray with elements from j + 1 to i is curr - (curr - k) = k.
> + Because the array can have negative numbers, the same prefix can occur multiple times. We use a hash map counts to track how many times a prefix has occurred.
> + At every index i, the frequency of curr - k is equal to the number of subarrays whose sum is equal to k that end at i. Add it to the answer.
![image](https://github.com/jiali120/DataStructure/assets/60761935/81b19664-d5e5-4281-ae95-9020ddfe8ea0)


### Reverse Word
+ 151. Reverse Words in a String
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/39b728e7-d231-4229-94d1-b4102bc6b97d)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/0ba4ef60-f95e-449c-a574-50884dc2919d)

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

557题：
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/25ef9d6d-323b-4142-b80e-abb6c8412ca3)

> ![image](https://github.com/jiali120/DataStructure/assets/60761935/d929aa46-f7dd-448b-8632-d51139aada26)

关于String in Java:  2000. Reverse Prefix of Word
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/81c52e94-035f-4c39-8233-8376e4c08c30)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/a55e0e51-2b1f-4421-9124-62d9de04ca71)


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







## Graphs DFS
[
 [1, 1, 0],
 [1, 1, 0],
 [0, 0, 1]
]
![image](https://github.com/jiali120/DataStructure/assets/60761935/021bdda5-9fbc-492d-8ce0-f0a2c058d37b)

![image](https://github.com/jiali120/DataStructure/assets/60761935/a3e7bf58-c469-4a6e-8232-b4008179c322)

Example： 547， 323
1. creat graph first
2. make "seen" marker for each node and call dfs()
3. creat dfs()
    ![image](https://github.com/jiali120/DataStructure/assets/60761935/a7bc1a19-29d4-472a-8642-2321d3c0f3b0)


200. Number of Islands
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/ffcf9fbb-d6aa-4f2c-8edc-faacebe4ad38)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/73e89bcc-2934-4864-bd77-fab926816d97)

[  ['1', '1', '0', '0', '0'],
  ['1', '1', '0', '0', '0'],
  ['0', '0', '1', '0', '0'],
  ['0', '0', '0', '1', '1']
]




![image](https://github.com/jiali120/DataStructure/assets/60761935/0675ab1d-a554-4c49-8ab6-21debabe2f24)
[  ['1', '1', '0', '0', '0'],
  ['1', '1', '0', '0', '0'],
  ['0', '0', '1', '0', '0'],
  ['0', '0', '0', '1', '1']
]
> 现在，我们将逐步通过 numIslands 函数：

> 开始 (row = 0, col = 0):

> 检查 grid[0][0]（值为 '1'），并未被访问过（seen[0][0] 为 false）。
> 增加岛屿数量 ans，执行 dfs(0, 0, grid) 来探索整个岛屿。
> dfs 会递归地探索所有相连的 '1'，将它们在 seen 中标记为已访问。
> 继续 (row = 0, col = 1):

> grid[0][1] 已在 dfs(0, 0, grid) 中被访问和标记，所以即使它是 '1'，numIslands 也不会对它进行处理。
> 跳过所有已访问的陆地，直到 (row = 0, col = 2):

> grid[0][2] 是 '0'，没有岛屿要探索。
> 直到 (row = 0, col = 4) 完成第一行的所有列。

> 前进到第二行 (row = 1, col = 0):

> grid[1][0] 和 grid[1][1] 在之前的 dfs 调用中已被探索和标记。
> 循环继续进行，直到 grid[1][2]，同样是 '0'。
> 到达 (row = 2, col = 2):

> 发现新的 '1'，这意味着发现了第二个岛屿。
> 执行 dfs(2, 2, grid)，探索这个岛屿。
> 最后，到达 (row = 3, col = 3):

> 发现 '1'，开始第三次 dfs 调用，探索最后一个岛屿。
> 通过这个过程，我们可以看到每个 '1' 最终都会被探索一次，numIslands 最终统计并返回了岛屿的数量，这个例子中的数量是 3。

## HashMap
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/3ae3c363-d3f1-47ac-9692-923e8ffdc952)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/0de11049-ba46-4676-bedc-be02bd9aad38)

##### 1189. Maximum Number of Balloons
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/bc55073c-fea8-4e83-a42f-becdb2c885c5)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/3bd3629e-8dcd-41fb-a4f9-cca531a6818d)
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/12eb50ae-c8e7-4508-82ad-662e819bd0b3)

* HashMap And Set
> ![image](https://github.com/jiali120/DataStructure/assets/60761935/29e38529-9478-41eb-912d-32bd30050dda)
> 383. Ransom Note

## Stacks and Queues
>  1. a stack followed a LIFO pattern(last in, first out); a queue follows FIFO (first in first out).
>  2. In a stack, elements are added and removed from the same side; In a queue, elements are added and removed from opposite sides.
>
> Queues:
> > // Declaration: Java supports multiple implementations, but we will using
> > // the Queue interface with the LinkedList implementation. Specify the data type
> > Queue<Integer> queue = new LinkedList<>();

> > // If you want to initialize it with some initial values:
> >Queue<Integer> queue = new LinkedList<>(Arrays.asList(1, 2, 3));

> > // Enqueueing/adding elements:
> >queue.offer(4);
> >queue.offer(5);

> > // Dequeuing/removing elements:
> >queue.poll(); // 1
> >queue.poll(); // 2

> > // Check if empty
> > queue.isEmpty(); // false

> > // Check element at front of queue (next element to be removed)
> > queue.peek(); // 3

> > // Get size
> > queue.size(); // 3

![image](https://github.com/jiali120/DataStructure/assets/60761935/2bf3d0ba-6515-45ac-a801-f65c83fb3548)
![image](https://github.com/jiali120/DataStructure/assets/60761935/d92ec895-ec04-49a1-8d09-e974a38b11f1)
![image](https://github.com/jiali120/DataStructure/assets/60761935/50f5e290-8592-48f1-a526-d4f4c79c20ab)


![image](https://github.com/jiali120/DataStructure/assets/60761935/080852e5-9ca7-4d1c-96f2-638e941c8f4c)
![image](https://github.com/jiali120/DataStructure/assets/60761935/8124acfe-eb77-4b6c-a34d-1a34ba20e8b6)
![image](https://github.com/jiali120/DataStructure/assets/60761935/eeba5bde-f210-47e8-97ec-f1045fcc8c42)
![image](https://github.com/jiali120/DataStructure/assets/60761935/8d8d91e2-1632-4fe7-b095-e0e270c95a4b)
![image](https://github.com/jiali120/DataStructure/assets/60761935/a705c58a-3bc7-471b-b920-475255a0c061)
![image](https://github.com/jiali120/DataStructure/assets/60761935/fa6c160c-08d9-456b-8071-71c9006f6818)



### Array
682. Baseball Game
> elif op == "+":
            > record.append(record[-1] + record[-2])
> record[-1] 是指 record 列表中的最后一个元素。这是 Python 中一种简便的索引方式，用来访问列表的倒数第几个元素; record[-2] 表示访问列表的倒数第二个元素，以此类推。






