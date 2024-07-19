

# 简单实现Promise/A+（构造函数）
我们自己要写一个Promise，肯定需要知道有哪些工作需要做，我们先从Promise的使用来窥探下需要做啥:
```
1. 新建Promise需要使用new关键字，那他肯定是作为面向对象的方式调用的，Promise是一个类。

2. 我们new Promise(fn)的时候需要传一个函数进去，说明Promise的参数是一个函数。

3. 构造函数传进去的fn会收到resolve和reject两个函数，用来表示Promise成功和失败，说明构造函数里面还需要resolve和reject这两个函数，这两个函数的作用是改变Promise的状态。

4. 根据规范，promise有pending，fulfilled，rejected三个状态，初始状态为pending，调用resolve会将其改为fulfilled，调用reject会改为rejected。

5. promise实例对象建好后可以调用then方法，而且是可以链式调用then方法，说明then是一个实例方法。链式调用的实现这篇有详细解释。简单的说就是then方法也必须返回一个带then方法的对象，可以是this或者新的promise实例。

