---

title:   iOS runtime 学习记录一

date:    2019-06-23 22:33:00 +0800

categories: [底层学习]

tags: [iOS, runtime, 底层]



---

# iOS runtime 学习记录一

>  摘要: 对于runtime一直是一知半解的状态打算利用空余时间好好学习与整理总结一下。

### 源码地址

[runtime](https://github.com/apple-oss-distributions/objc4/tags) 版本号 objc4-866.9

### runtime

iOS runtime 是 iOS 系统中的一个运行时库，负责管理 Objective-C 对象、类和方法等的创建、销毁和调用，实现了 Objective-C 的动态特性，并支持其他语言的绑定。

### 发送消息

> 还记得初学 Objective-C 时把 `[receiver message]` 当成简单的方法调用，而无视了**“发送消息”**这句话的深刻含义。

`[receiver message]`会被编译器转化为

```objc_msgSend(receiver, selector)```

如果消息含有参数，则为：

`objc_msgSend(receiver, selector, arg1, arg2, ...)`

### Runtime 基础数据结构
#### SEL
`typedef struct objc_selector *SEL;`