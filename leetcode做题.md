面试碰到了算法题  
决定在leetcode上做一些题目熟悉熟悉  
也可以用js语法  
还能熟悉基础语法  
  
  
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
