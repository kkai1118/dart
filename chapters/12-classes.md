# 12 补充：类和对象

对应主文档章节：`12. 类和对象`

## 为什么 Flutter 代码里到处都是类

Flutter 的页面、组件、配置对象、模型对象，本质上大量都通过类表达。

## 类的三个常见组成部分

```dart
class User {
  String name;
  int age;

  User(this.name, this.age);

  void sayHello() {
    print('hello, I am $name');
  }
}
```

- 字段：`name`、`age`
- 构造函数：`User(...)`
- 方法：`sayHello()`

## 类和对象分别是什么

可以先这样理解：

- 类：像一张设计图
- 对象：按照这张设计图创建出来的具体实例

比如：

```dart
class User {
  String name;
  int age;

  User(this.name, this.age);
}
```

这里 `User` 是类。

```dart
final user1 = User('Tom', 18);
final user2 = User('Jack', 20);
```

这里的 `user1`、`user2` 是对象。

## 怎么创建对象

最常见的方式就是调用构造函数：

```dart
final user = User('Tom', 18);
```

你可以把它理解成：

- `User(...)`：创建一个 `User` 对象
- `user`：用变量接住这个对象

## 字段是对象身上的数据

字段就是类里保存的数据。

```dart
class User {
  String name;
  int age;

  User(this.name, this.age);
}
```

这里：

- `name` 是字段
- `age` 是字段

创建对象后，可以这样访问：

```dart
final user = User('Tom', 18);
print(user.name);
print(user.age);
```

## 方法是对象能做的事情

方法就是写在类里的函数。

```dart
class User {
  String name;

  User(this.name);

  void sayHello() {
    print('hello, I am $name');
  }
}
```

调用时：

```dart
final user = User('Tom');
user.sayHello();
```

你可以这样记：

- 字段：对象有什么数据
- 方法：对象能做什么事

## `this.name` 是什么

表示“把传进来的参数赋值给当前对象的字段”。

比如：

```dart
class User {
  String name;

  User(this.name);
}
```

它相当于更完整的写法：

```dart
class User {
  String name;

  User(String name) : name = name;
}
```

入门阶段先把 `this.name` 理解成“当前对象自己的 name”就够了。

## 类里为什么经常写 `final`

很多对象创建后，字段就不希望再变了。

```dart
class User {
  final String name;
  final int age;

  User(this.name, this.age);
}
```

这样做的好处：

- 对象更稳定
- 不容易被误改
- 很适合模型对象、配置对象

## Flutter 里为什么类这么多

因为 Flutter 里大量东西本质上都是对象：

- 页面是对象
- 组件是对象
- 路由配置是对象
- 数据模型也是对象

比如：

```dart
Text('Hello')
```

本质上就是在创建一个 `Text` 对象。

```dart
Container(
  width: 100,
  height: 40,
)
```

本质上也是在创建一个 `Container` 对象。

## 读代码技巧

- 看到 `SomeClass(...)` 时，优先判断它是不是在创建对象实例
- 看到 `xxx.name` 这种写法时，通常是在访问对象字段
- 看到 `xxx.sayHello()` 这种写法时，通常是在调用对象方法
