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

这里的重点是：

- `User(...)` 还是默认构造函数
- `{required this.name, required this.age}` 是命名参数
- 调用时要写参数名

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

## 默认构造函数、命名参数、命名构造函数分别是什么

这三个概念很容易混。

### 1. 默认构造函数

```dart
class User {
  final String name;

  User(this.name);
}
```

这里的 `User(...)` 就是默认构造函数。

### 2. 默认构造函数 + 命名参数

```dart
class User {
  final String name;
  final int age;

  User({required this.name, required this.age});
}
```

这里还是默认构造函数，只是参数写成了命名参数。

### 3. 命名构造函数

```dart
class User {
  User.guest();
}
```

这里的 `User.guest()` 才是命名构造函数。

## 命名参数的好处

- 参数多时更清楚
- 不容易传错顺序
- 调用代码更像“配置项”

比如：

```dart
Container(
  width: 100,
  height: 40,
  color: Colors.blue,
)
```

如果这些参数全靠位置传，代码会很难读。

## `required` 为什么常和命名参数一起出现

```dart
class User {
  final String name;
  final int age;

  User({required this.name, required this.age});
}
```

含义是：

- 参数是命名参数
- 但调用时必须传

调用时：

```dart
User(name: 'Tom', age: 18);
```

如果漏掉 `name` 或 `age`，编译器会直接提醒你。

## 命名构造函数是干什么的

命名构造函数的作用通常是：提供“不同用途的创建方式”。

比如：

```dart
class User {
  final String name;
  final int age;

  User({required this.name, required this.age});

  User.guest()
      : name = 'guest',
        age = 0;
}
```

调用时：

```dart
User(name: 'Tom', age: 18);
User.guest();
```

这样一个类就可以有多种创建方式。

## 真实场景里常见的命名构造函数

### `guest`

表示创建默认游客对象。

### `fromJson`

表示从 JSON 数据创建对象。

```dart
class User {
  final String name;

  User({required this.name});

  User.fromJson(Map<String, dynamic> json) : name = json['name'];
}
```

### `empty`

表示创建一个空对象或初始对象。

## 和工厂构造函数先简单区分一下

你后面还会见到这种写法：

```dart
class User {
  factory User.fromCache() {
    return User(name: 'cached');
  }

  User({required this.name});

  final String name;
}
```

这里的 `factory` 也是构造函数的一种。

初学阶段先记：

- `User.guest()`：命名构造函数
- `factory User.fromCache()`：工厂构造函数

## 读代码技巧

- 看到 `User(...)`：通常是默认构造函数
- 看到 `User(name: ..., age: ...)`：通常是“默认构造函数 + 命名参数”
- 看到 `User.guest()`、`User.fromJson(...)`：通常是命名构造函数
