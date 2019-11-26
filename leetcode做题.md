面试碰到了算法题  
决定在leetcode上做一些题目熟悉熟悉  
也可以用js语法  
还能熟悉基础语法  
暂时先写简单难度(其他难度简直找虐,需要数据结构和算法的基础知识才能够进行解题)  

  
  
1.给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。  
你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。  
  
来源：力扣（LeetCode）  
链接：https://leetcode-cn.com/problems/two-sum  
  
<details>  
  
解题:  
1.遍历  
```
var twoSum = function(nums, target) {
    for(let i = 0; i < nums.length; i++) {
        for(let j = i + 1; j < nums.length ; j++) {
            if(nums[i] + nums[j] === target) {
                return [i,j];
            }
        }
    }
};  
```
188ms  
2.使用filter替代第一个for循环  
```
var twoSum = function(nums, target) {
    let i,j;
    nums.filter((num,index,nums) => {
        for(let k = index + 1,len = nums.length; k < len; k++) {
            if(num + nums[k] === target) {
                i = index;
                j = k;
                break;
            }
        }
    })
    return [i,j];
};
```
148ms  
  
其他解法不太看得懂,就这样吧先  

</details>  
  
7.给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。
```示例 1:

输入: 123
输出: 321
 示例 2:

输入: -123
输出: -321
示例 3:

输入: 120
输出: 21
```
注意:  
假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为 [−231,  231 − 1]。请根据这个假设，如果反转后整数溢出那么就返回 0。  
  
来源：力扣（LeetCode）  
链接：https://leetcode-cn.com/problems/reverse-integer  
  
<details>    
  
解题:  
转数组用数组reverse然后转回数字
```
var reverse = function(x) {
    let ans;
    let max = Math.pow(2,31);
    if(x < 0) {
        ans = Number.parseInt((-x).toString(10).split('').reverse().join(''));
        return (ans > max) ? 0: -ans;
    } else {
        ans = Number.parseInt(x.toString(10).split('').reverse().join(''));
        return (ans > max - 1) ? 0: ans;
    }
};
```
同样是暴力方法  
92ms  

</details> 
