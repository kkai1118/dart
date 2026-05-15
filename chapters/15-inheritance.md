# 15 补充：继承与重写

对应主文档章节：`15. 继承与重写`

## 基础关系

```dart
class Animal {
  void speak() {
    print('...');
  }
}

class Dog extends Animal {
  @override
  void speak() {
    print('wang');
  }
}
```

- `extends`：继承
- `@override`：重写父类方法

## 继承可以怎么理解

可以先把它理解成：

- 父类提供通用能力
- 子类在它基础上复用或定制

比如：

- `Animal` 是更通用的父类
- `Dog` 是更具体的子类

## 子类能得到什么

子类通常可以直接使用父类里的：

- 字段
- 方法
- 已有的通用逻辑

例如：

```dart
class Animal {
  void eat() {
    print('eat');
  }
}

class Dog extends Animal {}

void main() {
  final dog = Dog();
  dog.eat();
}
```

虽然 `Dog` 没有自己写 `eat()`，但它继承到了这个方法。

## 什么叫重写

如果父类有一个方法，子类想改成自己的实现，就叫重写。

```dart
class Animal {
  void speak() {
    print('...');
  }
}

class Dog extends Animal {
  @override
  void speak() {
    print('wang');
  }
}
```

这里 `Dog` 用自己的 `speak()` 替换了父类版本。

## 为什么要写 `@override`

- 让代码意图更清楚
- 编译器能帮你检查签名是否正确

## `super` 是什么

`super` 表示“父类那一层”。

### 调父类方法

```dart
class Animal {
  void speak() {
    print('...');
  }
}

class Dog extends Animal {
  @override
  void speak() {
    super.speak();
    print('wang');
  }
}
```

这里的 `super.speak()` 表示先执行父类版本。

### 调父类构造函数

```dart
class Animal {
  final String name;

  Animal(this.name);
}

class Dog extends Animal {
  Dog(String name) : super(name);
}
```

这里的 `super(name)` 是把参数传给父类构造函数。

## 抽象类 `abstract`

有些父类更像“规范”，不打算直接创建对象。

```dart
abstract class Animal {
  void speak();
}

class Dog extends Animal {
  @override
  void speak() {
    print('wang');
  }
}
```

这里：

- `Animal` 不能直接 `Animal()`
- 它更像是在规定：子类必须有 `speak()`

## `extends` 和 `implements` 先简单区分

### `extends`

- 继承父类实现
- 复用父类已有代码

### `implements`

- 更像“我承诺遵守这个接口”
- 但通常要自己把成员重新实现一遍

```dart
abstract class Runner {
  void run();
}

class Dog implements Runner {
  @override
  void run() {
    print('run');
  }
}
```

初学阶段先记：

- 想复用已有实现，先想到 `extends`
- 只想遵守一套规范，可能会看到 `implements`

## Flutter 中常见的“重写”

```dart
@override
Widget build(BuildContext context) {
  return Container();
}
```

这是你最常见的一种方法重写。

## Flutter 里为什么经常见到继承

比如：

- `StatelessWidget`
- `StatefulWidget`
- `State`

你自己写页面时，本质上就是在继承这些类，然后重写它们要求的方法。

例如：

```dart
class HomePage extends StatelessWidget {
  const HomePage({super.key});

  @override
  Widget build(BuildContext context) {
    return const Text('home');
  }
}
```

这里：

- `HomePage` 继承了 `StatelessWidget`
- 并重写了 `build`

## 读代码技巧

- 看到 `extends`：先判断谁是父类，谁是子类
- 看到 `@override`：说明子类正在改写父类或接口要求的方法
- 看到 `super.xxx`：说明这里在访问父类能力
