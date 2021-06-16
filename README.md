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

```
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 0
        if len(nums) == 1:
            return nums[0]
        if len(nums) == 2:
            return max([nums[0], nums[1], sum(nums)])
        max_sum = nums[0]
        for i in range(len(nums)):
            tmp_max_sum = nums[i]
            if tmp_max_sum > max_sum:
                max_sum = tmp_max_sum
            for j in range(i + 1, len(nums)):
                tmp_max_sum += nums[j]
                if tmp_max_sum > max_sum:
                    max_sum = tmp_max_sum
        return max_sum

class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 0
        if len(nums) == 1:
            return nums[0]
        if len(nums) == 2:
            return max([nums[0], nums[1], sum(nums)])
        max_sum = nums[0]
        tmp = max_sum
        for i in range(1, len(nums)):
            if tmp + nums[i] > nums[i]:
                max_sum = max(max_sum, tmp + nums[i])
                tmp += nums[i]
            else:
                max_sum = max(max_sum, tmp, nums[i])
                tmp = nums[i]
        return max_sum
```

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

```
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head or not head.next:
            return head
        cur = head
        prev = None
        while cur:
            tmp = cur.next
            cur.next = prev
            prev = cur
            cur = tmp
        return prev
```

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

#### 11. 盛最多水的容器

LeetCode地址: https://leetcode-cn.com/problems/container-with-most-water/

#### 15. 三数之和

LeetCode地址: https://leetcode-cn.com/problems/3sum/

#### 17. 电话号码的字母组合

LeetCode地址: https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/

#### 19. 删除链表的倒数第 N 个结点

LeetCode地址: https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/

#### 22. 括号生成

LeetCode地址: https://leetcode-cn.com/problems/generate-parentheses/

#### 31. 下一个排列

LeetCode地址: https://leetcode-cn.com/problems/next-permutation/

#### 33. 搜索旋转排序数组

LeetCode地址: https://leetcode-cn.com/problems/search-in-rotated-sorted-array/

#### 34. 在排序数组中查找元素的第一个和最后一个位置

LeetCode地址: https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/

#### 39. 组合总和

LeetCode地址: https://leetcode-cn.com/problems/combination-sum/

#### 46. 全排列

LeetCode地址: https://leetcode-cn.com/problems/permutations/

#### 48. 旋转图像

LeetCode地址: https://leetcode-cn.com/problems/rotate-image/

#### 49. 字母异位词分组

LeetCode地址: https://leetcode-cn.com/problems/group-anagrams/

#### 55. 跳跃游戏

LeetCode地址: https://leetcode-cn.com/problems/jump-game/

#### 56. 合并区间

LeetCode地址: https://leetcode-cn.com/problems/merge-intervals/

#### 62. 不同路径

LeetCode地址: https://leetcode-cn.com/problems/unique-paths/

#### 64. 最小路径和

LeetCode地址: https://leetcode-cn.com/problems/minimum-path-sum/

#### 75. 颜色分类

LeetCode地址: https://leetcode-cn.com/problems/sort-colors/

#### 78. 子集

LeetCode地址: https://leetcode-cn.com/problems/subsets/

#### 79. 单词搜索

LeetCode地址: https://leetcode-cn.com/problems/word-search/

#### 96. 不同的二叉搜索树

LeetCode地址: https://leetcode-cn.com/problems/unique-binary-search-trees/

#### 98. 验证二叉搜索树

LeetCode地址: https://leetcode-cn.com/problems/validate-binary-search-tree/

#### 102. 二叉树的层序遍历

LeetCode地址: https://leetcode-cn.com/problems/binary-tree-level-order-traversal/

#### 105. 从前序与中序遍历序列构造二叉树

LeetCode地址: https://leetcode-cn.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/

#### 114. 二叉树展开为链表

LeetCode地址: https://leetcode-cn.com/problems/flatten-binary-tree-to-linked-list/

#### 128. 最长连续序列

LeetCode地址: https://leetcode-cn.com/problems/longest-consecutive-sequence/

#### 139. 单词拆分

LeetCode地址: https://leetcode-cn.com/problems/word-break/

#### 142. 环形链表 II

LeetCode地址: https://leetcode-cn.com/problems/linked-list-cycle-ii/

#### 146. LRU 缓存机制

LeetCode地址: https://leetcode-cn.com/problems/lru-cache/

#### 148. 排序链表

LeetCode地址: https://leetcode-cn.com/problems/sort-list/

#### 152. 乘积最大子数组

LeetCode地址: https://leetcode-cn.com/problems/maximum-product-subarray/

#### 198. 打家劫舍

LeetCode地址: https://leetcode-cn.com/problems/house-robber/

#### 200. 岛屿数量

LeetCode地址: https://leetcode-cn.com/problems/number-of-islands/

#### 207. 课程表

LeetCode地址: https://leetcode-cn.com/problems/course-schedule/

#### 208. 实现 Trie (前缀树)

LeetCode地址: https://leetcode-cn.com/problems/implement-trie-prefix-tree/

#### 215. 数组中的第K个最大元素

LeetCode地址: https://leetcode-cn.com/problems/kth-largest-element-in-an-array/

#### 221. 最大正方形

LeetCode地址: https://leetcode-cn.com/problems/maximal-square/

#### 236. 二叉树的最近公共祖先

LeetCode地址: https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-tree/

#### 238. 除自身以外数组的乘积

LeetCode地址: https://leetcode-cn.com/problems/product-of-array-except-self/

#### 240. 搜索二维矩阵 II

LeetCode地址: https://leetcode-cn.com/problems/search-a-2d-matrix-ii/

#### 279. 完全平方数

LeetCode地址: https://leetcode-cn.com/problems/perfect-squares/

#### 287. 寻找重复数

LeetCode地址: https://leetcode-cn.com/problems/find-the-duplicate-number/

#### 300. 最长递增子序列

LeetCode地址: https://leetcode-cn.com/problems/longest-increasing-subsequence/

#### 309. 最佳买卖股票时机含冷冻期

LeetCode地址: https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/

#### 322. 零钱兑换

LeetCode地址: https://leetcode-cn.com/problems/coin-change/

#### 337. 打家劫舍 III

LeetCode地址: https://leetcode-cn.com/problems/house-robber-iii/

#### 347. 前 K 个高频元素

LeetCode地址: https://leetcode-cn.com/problems/top-k-frequent-elements/

#### 394. 字符串解码

LeetCode地址: https://leetcode-cn.com/problems/decode-string/

#### 399. 除法求值

LeetCode地址: https://leetcode-cn.com/problems/evaluate-division/

#### 406. 根据身高重建队列

LeetCode地址: https://leetcode-cn.com/problems/queue-reconstruction-by-height/

#### 416. 分割等和子集

LeetCode地址: https://leetcode-cn.com/problems/partition-equal-subset-sum/

#### 437. 路径总和 III

LeetCode地址: https://leetcode-cn.com/problems/path-sum-iii/

#### 438. 找到字符串中所有字母异位词

LeetCode地址: https://leetcode-cn.com/problems/find-all-anagrams-in-a-string/

#### 494. 目标和

LeetCode地址: https://leetcode-cn.com/problems/target-sum/

#### 538. 把二叉搜索树转换为累加树

LeetCode地址: https://leetcode-cn.com/problems/convert-bst-to-greater-tree/

#### 560. 和为K的子数组

LeetCode地址: https://leetcode-cn.com/problems/subarray-sum-equals-k/

#### 581. 最短无序连续子数组

LeetCode地址: https://leetcode-cn.com/problems/shortest-unsorted-continuous-subarray/

#### 621. 任务调度器

LeetCode地址: https://leetcode-cn.com/problems/task-scheduler/

#### 647. 回文子串

LeetCode地址: https://leetcode-cn.com/problems/palindromic-substrings/

#### 739. 每日温度

LeetCode地址: https://leetcode-cn.com/problems/daily-temperatures/

#### 1254. 统计封闭岛屿的数目

LeetCode地址: https://leetcode-cn.com/problems/number-of-closed-islands/

```
class Solution:
    def closedIsland(self, grid: List[List[int]]) -> int:
        if len(grid) == 0:
            return 0
        rows, cols = len(grid), len(grid[0])

        def dfs(x, y):
            if grid[x][y] == 1:
                return
            grid[x][y] = 1
            for xx, yy in [(x-1, y), (x, y+1), (x+1, y), (x, y-1)]:
                if 0 <= xx < rows and 0 <= yy < cols:
                    dfs(xx, yy)

        for i in range(rows):
            dfs(i, 0)
            dfs(i, cols - 1)
        
        for j in range(cols):
            dfs(0, j)
            dfs(rows - 1, j)

        count = 0
        for i in range(rows):
            for j in range(cols):
                if grid[i][j] == 0:
                    dfs(i, j)
                    count += 1
        
        return count
```

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