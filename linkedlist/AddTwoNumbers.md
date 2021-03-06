### Question - Add Two Numbers

You are given two non-empty linked lists representing two non-negative integers. 
The digits are stored in reverse order and each of their nodes contain a single digit. 
Add the two numbers and return it as a linked list.
You may assume the two numbers do not contain any leading zero, except the number 0 itself.

      Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
      Output: 7 -> 0 -> 8

[LeetCode Link](https://leetcode.com/problems/add-two-numbers/#/description)

### Understanding the problem

This is a very interesting problem which explains how integer addition can be done via linked lists. 
Consider addition of two numbers 342 and 465. The output of addition will be 807.

      3 4 2
    + 4 6 5
    --------
      8 0 7

Our question here says the input will be in the form of *linked lists* representing 342 and 465. 
Also, it says the digits are stored in __reverse order__ and each of their nodes contain a single digit. i.e.
linked list for 342 will be like -

      2 -> 4 -> 3 
      
linked list for 465 will be like -

      5 -> 6 -> 4

Also, as expected linked list for their sum (807) will be represented as linked list -

      7 -> 0 -> 8


**Umm, Could you think of why having the reverse order??**

Ok, think about how we actually perform addition. If we add these numbers we add it from right to left, 
i.e units place first. So we add 2 + 5 and then 4 + 6 and 3 + 4

Hence, having the inputs in reverse order makes our life easier!! Once we finish solving this, think of how you could solve the problem in case the inputs weren't in reverse order!!

**How do we perform addition by hand**
- We add the digits from right to left
- At each place while adding if the sum is greater than 9, we carry the digit over to next place and repeat the process. 

      Carry 0 1 0
            -----
            3 4 2
          + 4 6 5
          --------
            8 0 7
      
On the basis of the above logic, let's jump onto framing the pseudo code!!


### Pseudo Code

      SUM (ListNode l1, ListNode l2):
        //Handle edge cases like l1 is null, l2 is null or both are null.
        Initialize sumList as empty linked list to store sum.
        Assign runners for l1 and l2 say runner1 and runner2
        Assign carry = 0
        Iterate while runner1 or runner2 is not null
            Assign sum = sum of values of runner1 and runner2 and carry
            Assign carry = sum / 10
            Assign sum = sum % 10
            Store sum in the sumList
        if carry is remaining at the end
            Append carry to the sumList

### Analysis of pseudo code
- For the inputs we have two lists l1, l2
- It is always good to handle edge cases in the beginning of the method to avoid running into exceptions.
- We use runner approach for iterating over the linkedlists.
      
      
### Test Cases
1. l1 can be null or l2 can be null or l1 and l2 can be null
2. 103 + 103 - Simple addition
3. 109 + 109 - Handling carry overs
4. 900 + 967 - Handling carry overs at the end

### Java Implementation
[Try it here](https://codebunk.com/b/680158836/)

Code can be found [here](https://github.com/hkasera/sturdy-spork/blob/master/linkedlist/code/AddTwoNumbers.java)


### Complexity Analysis
Let's say the inputs l1 and l2 are of size m and n respectively. 

#### Time Complexity -
Our code iterates over the linkedlists and hence will run in the order of m+n.
Hence, time complexity is O(m + n) where m and n are number of nodes in l1 and l2 respectively.

#### Space Complexity -
In the solution, we create a sumList of size m+n.
Hence, space complexity is O(m + n) where m and n are number of nodes in l1 and l2 respectively.

  

  
