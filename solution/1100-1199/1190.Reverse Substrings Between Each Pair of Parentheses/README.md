# [1190. 反转每对括号间的子串](https://leetcode-cn.com/problems/reverse-substrings-between-each-pair-of-parentheses)

[English Version](/solution/1100-1199/1190.Reverse%20Substrings%20Between%20Each%20Pair%20of%20Parentheses/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>给出一个字符串&nbsp;<code>s</code>（仅含有小写英文字母和括号）。</p>

<p>请你按照从括号内到外的顺序，逐层反转每对匹配括号中的字符串，并返回最终的结果。</p>

<p>注意，您的结果中 <strong>不应</strong> 包含任何括号。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>s = &quot;(abcd)&quot;
<strong>输出：</strong>&quot;dcba&quot;
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>s = &quot;(u(love)i)&quot;
<strong>输出：</strong>&quot;iloveu&quot;
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>s = &quot;(ed(et(oc))el)&quot;
<strong>输出：</strong>&quot;leetcode&quot;
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>s = &quot;a(bcdefghijkl(mno)p)q&quot;
<strong>输出：</strong>&quot;apmnolkjihgfedcbq&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 2000</code></li>
	<li><code>s</code> 中只有小写英文字母和括号</li>
	<li>我们确保所有括号都是成对出现的</li>
</ul>


## 解法

<!-- 这里可写通用的实现逻辑 -->

用双端队列或者栈，模拟反转过程

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python
class Solution:
    def reverseParentheses(self, s: str) -> str:
        stack = []
        for c in s:
            if c == ")":
                tmp = []
                while stack[-1] != "(":
                    tmp += stack.pop()
                stack.pop()
                stack += tmp
            else:
                stack.append(c)
        return "".join(stack)
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java
class Solution {
    public String reverseParentheses(String s) {
        Deque<Character> deque = new ArrayDeque<>();
        for (char c : s.toCharArray()) {
            if (c == ')') {
                StringBuilder sb = new StringBuilder();
                while (deque.peekLast() != '(') {
                    sb.append(deque.pollLast());
                }
                deque.pollLast();
                for (int i = 0, n = sb.length(); i < n; i++) {
                    deque.offerLast(sb.charAt(i));
                }
            } else {
                deque.offerLast(c);
            }
        }
        StringBuilder sb = new StringBuilder();
        while (!deque.isEmpty()) {
            sb.append(deque.pollFirst());
        }
        return sb.toString();
    }
}
```

### **...**

```

```

<!-- tabs:end -->
