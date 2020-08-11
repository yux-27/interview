浏览器工作原理与实践


笔记

HTTP 请求分为三个部分： TCP 三次握手、http 请求响应信息、关闭 TCP 连接


相关面试题


#### 输入url到页面呈现发生了什么

+ DNS 解析：将域名解析成IP地址
+ TCP 连接：TCP 三次握手
+ 发送 HTTP 请求
+ 服务器处理请求并返回 HTTP 报文
+ 浏览器解析渲染页面
+ 断开连接：TCP 四次握手

[参考文章](https://zhuanlan.zhihu.com/p/57895541)


#### TCP 三次握手

客户端发起连接请求=》服务器确认连接请求=》客户端确认收到确认连接请求=》服务器等待接收请求、客户端发送请求


#### Event Loop

流程图如下：

![event-loop](https://tang-yue.github.io/fe-interview/promise/event-loop.jpg)


总结：

先执行宏任务，后执行微任务，同步任务立即执行，异步任务将回调函数放入Event Queue等待下一轮事件循环


具体流程：

1、执行全局Script 代码，这些代码中有同步语句或异步语句，遇到同步语句直接执行，异步语句放入宏任务或微任务的队列。

2、全局 Script 代码执行完毕后，调用栈 Stack 会清空

3、从微任务中取出位于队首的回调任务，放入调用栈Stack 中执行，执行完成后，微任务队列长度减一

4、继续取出位于队首的任务，放入调用栈 Stack 中执行，以此类推，直到把微任务队列中的所有任务都执行完毕，注意，如果在执行微任务过程中，又产生了新的微任务，那么会加入到微任务队列的尾部，也会在这个周期被执行

5、当微任务队列中所有任务都执行完毕后，此时微任务队列为空，调用栈Stack 也会为空

6、取出 宏任务中的队首的任务放入 Stack 中执行

7、执行完毕后，调用栈 Stack 为空

8、重复第3～7个步骤

9、重复3～7 步骤



[参考文章](https://zhuanlan.zhihu.com/p/165149415)



