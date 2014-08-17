---
layout: post
title: Elixir web frameworks
date: 2014-08-11 20:48:31
---

Elixir社区现有和几个web开发框架:

* [dynamo](https://github.com/dynamo/dynamo)
* [phoenix](https://github.com/phoenixframework/phoenix)
* [sugar](https://github.com/sugar-framework/sugar)
* [weber](https://github.com/elixir-web/weber)

另外，还有[plug](https://github.com/elixir-lang/plug) 
plug不是一个web框架，是一个类似Ruby中Rack的基础库，为中间件提供统一的api


---

## 状态

### dynamo 

dynamo 是Elixir作者开发的，不过作者说项目已经进入维护状态，不建议选择
另外 dynamo 比 plug 项目要早，不是基于plug项目。

### sugar

这个框架也是基于plug的，不过作者已经把这个项目作为一个`educational project`，作者还建议你如果在生产环境中使用 phoenix

### phoenix

phoenix 是Elixir社区关注度比较高的web框架，基于plug。

特点: 

* DSL Routing, 支持resource
* 支持websocket
* code reload
* 提供了Topic的概念，简单的publish/subscribe机制
* ...

具体可以看 [Feature Roadmap](https://github.com/phoenixframework/phoenix#feature-roadmap)


### weber

基于plug，关注度感觉不如 phoenix, 目前为止感觉 phoenix开发上更活跃一些。


