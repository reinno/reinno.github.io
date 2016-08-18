---
layout: post
title: "使用AKKA http增强gitlab api"
---

## 配置
### typesafe config
* 命令行对配置的覆盖
java -Dconfig.file=xx -jar xx.java
java -Dxx.xx=xx -jar xx.java

###

### 配置的持久化

## 结构设计
* 树形

## 消息设计
* 消息的归属

## vs FSM
FSM无法直接使用future，必须将future pipeTo self，这样Actor就不会阻塞，但写作更繁复

普通actor和FSM actor都可以有一般变量，而FSM还有随状态机迁移的变量(可以参与消息接收时的模式匹配，类似不同维度的状态)

## supervisor vs watch
supervisor 中的处理无法使用actor中的数据，只有context和actorRef，可以通过自定义Exception的方式将需要的数据携带出来。但



## akka-http

## 依赖注入

## 测试
### Mock
Mock的目的在于模拟被测对象和周围环境的交互过程，检查输出，模拟输入，而之所以需要Mock的原因还在于输入和输出的边界不只有测试框架直接接触的接口，否则直接使用出入参进行测试就行了。从这个角度来讲，Mock需要辅助测试的是被测对象的副作用，而Mock正是将这些原来认为有副作用的部分通过补充接口监控的方式转化为无副作用。
对于难于Mock的对象，使用函数式的思想，将有副作用和无副作用的部分分开，扩大无副作用的占比，简化有副作用的逻辑，分别进行测试的方法仍然适用。
内部使用Actor系统以后，内部Actor的交互都以Actor消息作为边界，Akka提供了TestProb能够很好地进行进行接口的模拟，对于这种场景，问题就在于如何将TestProb注入到测试场景中。
除了Actor消息以外的边界，比如和数据库的交互，使用Http Client和外部的交互

## 构建

### Plugin
