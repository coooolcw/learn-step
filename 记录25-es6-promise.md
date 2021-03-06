深入理解ES6 p.235  
  
MDN  promise的使用  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Using_promises#%E7%BA%A6%E5%AE%9A  
  
MDN promise基本概念  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise  
  
ES6入门  
http://es6.ruanyifeng.com/#docs/promise  
  
  
深入理解ES6除了nodejs部分其他部分较为容易理解  
api介绍由浅入深  
es6可作为api补充查看  
你不知道的js  p136 讲得更清楚但是过于深入,留待未来进一步学习  
  
基本语法  
`new Promise( function(resolve, reject) {...} /* executor */  );`
executor  
executor是带有 resolve 和 reject 两个参数的函数。  
Promise构造函数执行时立即调用executor 函数， resolve 和 reject 两个函数作为参数传递给executor  
（executor 函数在Promise构造函数返回所建promise实例对象前被调用）。  
resolve 和 reject 函数被调用时，分别将promise的状态改为fulfilled(完成)或rejected(失败)。  
executor 内部通常会执行一些异步操作，一旦异步操作执行完毕(可能成功/失败)，  
要么调用resolve函数来将promise状态改成fulfilled，要么调用reject 函数将promise的状态改为rejected。  
如果在executor函数中抛出一个错误，那么该promise 状态为rejected。executor函数的返回值被忽略。  
  
基本概念非常复杂,略  
使用重点  
深入理解es6p258  
return一个新的promise达成目的:一个promise解决后再触发下一个  
  
书籍上普遍未提到的finally  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/finally  
  
1.Promise.all()  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/all  
如果传入的参数是一个空的可迭代对象，则返回一个已完成（already resolved）状态的 Promise。  
2.Promise.race()  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/race  
如果传的迭代是空的，则返回的 promise 将永远等待。  
  
3.Promise.resolve()  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve  
如果这个值是个thenable（即带有then方法），返回的promise会“跟随”这个thenable的对象，  
采用它的最终状态（指resolved/rejected/pending/settled）；  
如果传入的value本身就是promise对象，则该对象作为Promise.resolve方法的返回值返回；  
否则以该值为成功状态返回promise对象。  
  
重点:resolve thenable的对象  
见深入理解es6 p245  
  
4.Promise.reject()  
Promise.reject()方法的参数，会原封不动地作为reject的理由，变成后续方法的参数。这一点与Promise.resolve方法不一致。  
```
const thenable = {
    then(resolve, reject) {
        reject('出错了');
    }
};
Promise.reject(thenable)
    .catch(e => {
        console.log(e === thenable)
})
// true
```
  
未来重点   
1.await  
已经标准化,支持尚可,挖坑待填  
2.rejectionhandled方法处理未被处理的错误promise  
https://developer.mozilla.org/en-US/docs/Web/API/Window/rejectionhandled_event  
  
注意细节:  
1.在promise中调用多次resolve,只有第一次调用生效  
2.在resolve和reject中只能传递一个参数  
3.Promise链的返回值可以是值也可以是promise对象.深入理解es6p255开始  
