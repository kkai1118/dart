# 03 补充：变量 `var`、`final`、`const`

对应主文档章节：`3. 变量：var、final、const`

## 一张对照表

| 写法 | 是否可重新赋值 | 值何时确定 | 常见用途 |
| --- | --- | --- | --- |
| `var` | 可以 | 运行时 | 临时变量 |
| `final` | 不可以 | 运行时 | 大多数局部变量 |
| `const` | 不可以 | 编译时 | 常量、常量 Widget |

## 三个最常见误区

### 1. `var` 不是动态类型

```dart
var count = 1;
// count = '1'; // 不可以
```

### 2. `final` 不是“绝对不可变”

```dart
final list = [1, 2];
list.add(3); // 可以，变的是对象内容
```

### 3. `const` 比 `final` 更严格

```dart
final now = DateTime.now(); // 可以
// const now = DateTime.now(); // 不可以
```

## 变量的作用域范围

先记一句话：变量通常只能在“它被声明的那一层”及其内部使用。

## 最常见的三种范围

### 1. 函数内局部变量

```dart
void main() {
  var name = 'Tom';
  print(name);
}
```

这里的 `name` 只能在 `main` 函数内部使用。

### 2. 代码块内变量

```dart
void main() {
  if (true) {
    var age = 18;
    print(age);
  }

  // print(age); // 不可以，age 超出作用域了
}
```

像 `if`、`for`、`while`、`{}` 代码块里声明的变量，出了这层代码块就不能用了。

### 3. 类中的字段

```dart
class User {
  String name = 'Tom';

  void sayHello() {
    print(name);
  }
}
```

这里的 `name` 是类的字段，只要在这个对象内部方法里，通常都可以访问。

## 一个常见现象：内层可以访问外层

```dart
void main() {
  var city = 'Shanghai';

  if (true) {
    print(city);
  }
}
```

内层代码块通常可以访问外层已经声明好的变量。

## 读代码时怎么理解作用域

- 先看变量在哪一层声明
- 再看当前代码是不是还在这层范围内
- 如果超出 `{}`、函数、类的可访问范围，就不能直接用

## Flutter 中的经验

- 默认优先考虑 `final`
- 值明显固定时用 `const`
- 只有确实会变化时才用 `var`
