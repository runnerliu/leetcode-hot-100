##### 本文整理 [LeetCode](https://leetcode-cn.com/problem-list/2cktkvj/) 热题100的思路及解决方法

### 简单

#### 1. 两数之和

LeetCode地址: https://leetcode-cn.com/problems/two-sum/

```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        if not nums:
            return []
        usedNums = {}
        for index, num in enumerate(nums):
            v = target - num
            if v in usedNums:
                return [usedNums[v], index]
            else:
                usedNums[num] = index
        return []
```

#### 20. 有效的括号

LeetCode地址: https://leetcode-cn.com/problems/valid-parentheses/

```
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        while '{}' in s or '()' in s or '[]' in s:
            s = s.replace('{}', '')
            s = s.replace('[]', '')
            s = s.replace('()', '')
        return s == ''
```

#### 21. 合并两个有序链表

LeetCode地址: https://leetcode-cn.com/problems/merge-two-sorted-lists/

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        if not l1: return l2
        if not l2: return l1
        if l1.val < l2.val:
            l1.next = self.mergeTwoLists(l1.next, l2)
            return l1
        else:
            l2.next = self.mergeTwoLists(l2.next, l1)
            return l2
```

#### 53. 最大子序和

LeetCode地址: https://leetcode-cn.com/problems/maximum-subarray/

#### 70. 爬楼梯

LeetCode地址: https://leetcode-cn.com/problems/climbing-stairs/

#### 94. 二叉树的中序遍历

LeetCode地址: https://leetcode-cn.com/problems/binary-tree-inorder-traversal/

#### 101. 对称二叉树

LeetCode地址: https://leetcode-cn.com/problems/symmetric-tree/

#### 104. 二叉树的最大深度

LeetCode地址: https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/

#### 121. 买卖股票的最佳时机

LeetCode地址: https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/

#### 136. 只出现一次的数字

LeetCode地址: https://leetcode-cn.com/problems/single-number/

#### 141. 环形链表

LeetCode地址: https://leetcode-cn.com/problems/linked-list-cycle/

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: ListNode) -> bool:
        if not head or not head.next:
            return False
        slow = fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                return True
        return False
```

#### 155. 最小栈

LeetCode地址: https://leetcode-cn.com/problems/min-stack/

#### 160. 相交链表

LeetCode地址: https://leetcode-cn.com/problems/intersection-of-two-linked-lists/

#### 169. 多数元素

LeetCode地址: https://leetcode-cn.com/problems/majority-element/

#### 206. 反转链表

LeetCode地址: https://leetcode-cn.com/problems/reverse-linked-list/

#### 226. 翻转二叉树

LeetCode地址: https://leetcode-cn.com/problems/invert-binary-tree/

#### 234. 回文链表

LeetCode地址: https://leetcode-cn.com/problems/palindrome-linked-list/

#### 283. 移动零

LeetCode地址: https://leetcode-cn.com/problems/move-zeroes/

```
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        if not nums:
            return []
        if 0 not in nums:
            return nums
        for i in range(len(nums)):
            if nums[i] == 0:
                for j in range(i, len(nums)):
                    if nums[j] != 0:
                        nums[i], nums[j] = nums[j], nums[i]
                        break
        return nums

class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        if not nums:
            return []
        if 0 not in nums:
            return nums
        count = i = 0
        while i < len(nums):
            if nums[i] == 0:
                del nums[i]
                count += 1
            else:
                i += 1
        nums.extend([0]*count)
        return nums
```

#### 448. 找到所有数组中消失的数字

LeetCode地址: https://leetcode-cn.com/problems/find-all-numbers-disappeared-in-an-array/

#### 461. 汉明距离

LeetCode地址: https://leetcode-cn.com/problems/hamming-distance/

#### 543. 二叉树的直径

LeetCode地址: https://leetcode-cn.com/problems/diameter-of-binary-tree/

#### 617. 合并二叉树

LeetCode地址: https://leetcode-cn.com/problems/merge-two-binary-trees/

### 中等

#### 2. 两数相加

LeetCode地址: https://leetcode-cn.com/problems/add-two-numbers/

```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        head = ListNode(l1.val + l2.val)
        cur = head
        while l1.next or l2.next:
            l1 = l1.next if l1.next else ListNode()
            l2 = l2.next if l2.next else ListNode()
            cur.next = ListNode(l1.val + l2.val + cur.val // 10)
            cur.val = cur.val % 10
            cur = cur.next
        if cur.val >= 10:
            cur.next = ListNode(cur.val // 10)
            cur.val = cur.val % 10
        return head
```

#### 3. 无重复字符的最长子串

LeetCode地址: https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/

#### 5. 最长回文子串

LeetCode地址: https://leetcode-cn.com/problems/longest-palindromic-substring/

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

LeetCode地址: 

### 困难

#### 4. 寻找两个正序数组的中位数

LeetCode地址: https://leetcode-cn.com/problems/median-of-two-sorted-arrays/

#### 10. 正则表达式匹配

LeetCode地址: https://leetcode-cn.com/problems/regular-expression-matching/

#### 23. 合并K个升序链表

LeetCode地址: https://leetcode-cn.com/problems/merge-k-sorted-lists/

#### 32. 最长有效括号

LeetCode地址: https://leetcode-cn.com/problems/longest-valid-parentheses/

```
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        if not s: return 0
        stack, l = [], 0
        for i in range(len(s)):
            if not stack or s[i] == '(' or s[stack[-1]] == ')':
                stack.append(i)
            else:
                stack.pop()
                l = max(l, i - (stack[-1] if stack else -1))
        return l
```

#### 42. 接雨水

LeetCode地址: https://leetcode-cn.com/problems/trapping-rain-water/

#### 72. 编辑距离

LeetCode地址: https://leetcode-cn.com/problems/edit-distance/

#### 76. 最小覆盖子串

LeetCode地址: https://leetcode-cn.com/problems/minimum-window-substring/

#### 84. 柱状图中最大的矩形

LeetCode地址: https://leetcode-cn.com/problems/largest-rectangle-in-histogram/

#### 85. 最大矩形

LeetCode地址: https://leetcode-cn.com/problems/maximal-rectangle/

#### 124. 二叉树中的最大路径和

LeetCode地址: https://leetcode-cn.com/problems/binary-tree-maximum-path-sum/

#### 128. 最长连续序列

LeetCode地址: https://leetcode-cn.com/problems/longest-consecutive-sequence/

#### 239. 滑动窗口最大值

LeetCode地址: https://leetcode-cn.com/problems/sliding-window-maximum/

#### 297. 二叉树的序列化与反序列化

LeetCode地址: https://leetcode-cn.com/problems/serialize-and-deserialize-binary-tree/

#### 301. 删除无效的括号

LeetCode地址: https://leetcode-cn.com/problems/remove-invalid-parentheses/

#### 312. 戳气球

LeetCode地址: https://leetcode-cn.com/problems/burst-balloons/