## 题目

编写一个函数，其作用是将输入的字符串反转过来。输入字符串以字符数组 char[] 的形式给出。

不要给另外的数组分配额外的空间，你必须原地修改输入数组、使用 O(1) 的额外空间解决这一问题。

你可以假设数组中的所有字符都是 ASCII 码表中的可打印字符。

示例 1：

输入：["h","e","l","l","o"]
输出：["o","l","l","e","h"]
示例 2：

输入：["H","a","n","n","a","h"]
输出：["h","a","n","n","a","H"]

## 思路

1. 双指针。
    - 使用left左指针记录左边的字符
    - 使用right右指针记录右边的字符
    - 左右指针往中间移动，交换左右指针对应的字符
    - 如果左指针大于右指针，循环终止
2. 同第一种方法，区别在于使用异或计算交换字符。测试的发现，并没有省多少空间，反而耗时更长了。

## 代码

### 方法1

```php
class Solution {

    /**
     * @param String[] $s
     * @return NULL
     */
    function reverseString(&$s) {
        $total = count($s);
        $left = 0;
        $right = $total - 1;

        while ($left <= $right) {
            $tmp = $s[$right];
            $s[$right] = $s[$left];
            $s[$left] = $tmp;

            $left++;
            $right--;
        }
    }
}
```

### 方法2

```php
class Solution {

    /**
     * @param String[] $s
     * @return NULL
     */
    function reverseString(&$s) {
        $total = count($s);
        $left = 0;
        $right = $total - 1;

        while ($left < $right) {
            $s[$left] ^= $s[$right];
            $s[$right] ^= $s[$left];
            $s[$left] ^= $s[$right];

            $left++;
            $right--;
        }
    }
}
```