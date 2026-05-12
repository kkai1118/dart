# 13 补充：命名构造参数

对应主文档章节：`13. 命名构造参数`

## 这和“命名构造函数”不是一回事

本章节说的是：构造函数里使用命名参数。

```dart
class User {
  final String name;
  final int age;

  User({required this.name, required this.age});
}
```

## 为什么这种写法很适合 Flutter

调用时非常清楚：

```dart
User(name: 'Tom', age: 18)
```

比起：

```dart
User('Tom', 18)
```

可读性更高，尤其参数一多时差别非常明显。

## 顺手补一个概念：命名构造函数

这是另一种语法：

```dart
class User {
  User.guest();
}
```

它和“命名参数”名字相似，但概念不同。
