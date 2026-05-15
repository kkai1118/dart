# 26 补充：下一步怎么学

对应主文档章节：`26. 下一步怎么学`

## 建议你现在就做的三件事

1. 打开 `lib/main.dart`，确认自己能解释每一行在做什么
2. 打开 `lib/app/app.dart`，确认自己能解释命名参数和 `MaterialApp`
3. 打开 `lib/app/router/app_router.dart`，确认自己能解释 `static`、`switch`、`RouteSettings`

## 如果你手边没有现成 Flutter 项目

那就先自己做一个最小练习：

1. 写一个 `main()` 入口
2. 写一个 `MaterialApp`
3. 写一个 `Scaffold`
4. 放一个 `Text`
5. 再加一个按钮和一个列表

这样能把 Dart 基础和 Flutter 页面连接起来。

## 一个 3 天练习计划

### 第 1 天

- 抄写变量、函数、类的基础例子
- 自己写一个 `User` 类

### 第 2 天

- 练习 `List`、`Map`、`if`、`for`
- 自己写 3 个字符串插值例子

### 第 3 天

- 练习 `Future`、`async`、`await`
- 回到 Flutter 项目里看路由和页面代码

## 怎么把 Dart 知识迁移到 Flutter 项目里

建议按这个顺序看：

### 1. 先看入口

看 `main.dart`：

- 程序从哪里启动
- `runApp(...)` 传了什么

### 2. 再看应用壳子

看 `MaterialApp`：

- 首页是谁
- 路由配置在哪里
- 主题有没有配置

### 3. 再看页面文件

看页面时，优先找：

- `Scaffold`
- `AppBar`
- `body`
- `child` / `children`

### 4. 最后再看交互和数据

比如：

- `onPressed`
- `onTap`
- `Future`
- `Navigator.push`

这样会比一上来钻进细节更容易看懂。

## 学完 Dart 之后最值得继续学的 Flutter 方向

- Widget 和布局
- 页面跳转
- 表单和输入
- 状态管理
- 网络请求
- JSON 解析
- 项目目录结构

## 一个很实用的下一步目标

给自己定一个小目标：独立写出一个“列表页 + 详情页 + 按钮点击 + 异步加载”的 demo。

如果你能完成这个小项目，通常说明 Dart 基础已经能真正用起来了。

## 学习完成的标志

如果你能独立解释这几个概念，说明已经入门：

- 为什么 `final List` 还能 `add`
- 为什么 `debugPrint(123)` 会报错
- 为什么 `String?` 不能直接赋给 `String`
- 为什么 Flutter 构造函数经常用命名参数

再往前一步，你还可以检查自己能不能做到：

- 看懂一个简单页面的 Widget 树
- 看懂一个按钮点击回调里的逻辑
- 看懂一个 `Future` 请求数据的流程
- 看懂一个对象是怎么从 JSON 创建出来的
