# 19 补充：Flutter 中最常见的 Dart 代码

对应主文档章节：`19. Flutter 中最常见的 Dart 代码`

## 看 Flutter 代码的建议顺序

看到一段 UI 代码时，优先按下面顺序读：

1. 这是在创建哪个类的实例
2. 传了哪些命名参数
3. 哪些参数是回调函数
4. 哪些地方用了 `const`

再补一个很实用的习惯：

5. 这一层的 `children` 或 `child` 里面又包了什么

因为 Flutter 代码经常就是一层一层往里包。

## 典型例子

```dart
MaterialApp(
  title: 'Home',
  onGenerateRoute: AppRouter.onGenerateRoute,
)
```

拆开看：

- `MaterialApp`：创建一个对象
- `title:`：命名参数
- `AppRouter.onGenerateRoute`：把静态方法作为参数传进去

## 再看一个更像真实页面的例子

```dart
Scaffold(
  appBar: AppBar(
    title: const Text('Home'),
  ),
  body: Column(
    children: [
      Text('Hello, $name'),
      ElevatedButton(
        onPressed: () {
          Navigator.push(
            context,
            MaterialPageRoute(
              builder: (context) => const DetailPage(),
            ),
          );
        },
        child: const Text('Go'),
      ),
    ],
  ),
)
```

## 这段代码怎么拆

### 第 1 层：最外层骨架

- `Scaffold`：页面骨架
- `appBar`：顶部栏
- `body`：主体内容

### 第 2 层：主体布局

- `Column`：纵向排列
- `children`：里面放多个子组件

### 第 3 层：具体组件

- `Text('Hello, $name')`：字符串插值
- `ElevatedButton(...)`：按钮组件

### 第 4 层：回调函数

```dart
onPressed: () {
  ...
}
```

这里传进去的是一个函数，也就是回调。

### 第 5 层：页面跳转

```dart
Navigator.push(...)
```

这里通常是在调用一个静态方法来跳转页面。

## 在 Flutter 代码里常同时看到哪些 Dart 知识点

一小段 UI 代码里，经常同时混着这些概念：

- 类实例化：`Text(...)`、`Container(...)`
- 命名参数：`title:`、`child:`、`onPressed:`
- 匿名函数：`() { ... }`
- 字符串插值：`'Hello, $name'`
- `const`：`const Text('Go')`
- 静态成员或静态方法：`Navigator.push(...)`

所以初学者看到 Flutter 代码会觉得“信息量很大”，其实只是很多基础 Dart 语法被同时放在了一起。

## 为什么 Flutter 代码看起来像“函数嵌套函数”

本质上很多地方是在连续创建对象，只是写成树状结构。

更准确一点说，常见是这几层同时出现：

- 对象里包对象
- 参数里再传对象
- 参数里再传函数

所以看起来会像：

- 函数套函数
- 括号套括号
- 花括号套花括号

但本质上你只要分层看，就不会那么乱。

## 一个很实用的阅读顺序

看到复杂 Widget 树时，建议这样读：

1. 先找最外层组件是什么
2. 再找 `child` / `children`
3. 再看每一层主要参数
4. 最后再看回调函数里的逻辑

不要一上来就钻进最里层按钮点击逻辑，不然很容易丢掉整体结构。

## 一句话总结

Flutter 代码并不是一种新的神秘语法，它大多数时候只是把这些 Dart 能力写在了一起：

- 类
- 构造函数
- 命名参数
- 匿名函数
- 字符串插值
- `const`
