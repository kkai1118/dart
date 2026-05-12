# Dart 快速入门

这份文档的目标只有一个：让你能尽快看懂并写出基础 Dart / Flutter 代码。

建议学习顺序：

1. 先通读一遍
2. 再对照项目代码回看
3. 最后自己手敲示例

补充阅读：

- 章节补充目录：`dart/chapters/README.md`

## 目录

- [1. Dart 是什么](#toc-01)
- [2. 第一个 Dart 程序](#toc-02)
- [3. 变量：var、final、const](#toc-03)
- [4. 基础类型](#toc-04)
- [5. 字符串插值](#toc-05)
- [6. 条件判断](#toc-06)
- [7. 循环](#toc-07)
- [8. 集合：List、Map、Set](#toc-08)
- [9. 函数](#toc-09)
- [10. 参数：位置参数、命名参数](#toc-10)
- [11. 空安全](#toc-11)
- [12. 类和对象](#toc-12)
- [13. 命名构造参数](#toc-13)
- [14. getter](#toc-14)
- [15. 继承与重写](#toc-15)
- [16. 异步：Future、async、await](#toc-16)
- [17. 异常处理](#toc-17)
- [18. import](#toc-18)
- [19. Flutter 中最常见的 Dart 代码](#toc-19)
- [20. print、debugPrint、log 的区别](#toc-20)
- [21. 初学者常见坑](#toc-21)
- [22. 推荐书写习惯](#toc-22)
- [23. 学习路线](#toc-23)
- [24. 10 个高频例子](#toc-24)
- [25. 一页速记](#toc-25)
- [26. 下一步怎么学](#toc-26)

<a id="toc-01"></a>
## 1. Dart 是什么 · [查看补充](chapters/01-overview.md)

- Dart 是 Flutter 的主要开发语言
- 语法风格接近 Java、JavaScript、TypeScript、C#
- Flutter 项目里最常见的是：
  - 变量
  - 函数
  - 类
  - 空安全
  - 集合
  - 异步

<a id="toc-02"></a>
## 2. 第一个 Dart 程序 · [查看补充](chapters/02-first-program.md)

```dart
void main() {
  print('Hello Dart');
}
```

含义：

- `void`：没有返回值
- `main`：程序入口
- `print(...)`：控制台输出

<a id="toc-03"></a>
## 3. 变量：var、final、const · [查看补充](chapters/03-variables.md)

### `var`

让 Dart 自动推断类型。

```dart
var name = 'Tom';
var age = 18;
```

等价于：

```dart
String name = 'Tom';
int age = 18;
```

特点：

- 类型推断后就固定了
- 变量后续可以重新赋值

```dart
var count = 1;
count = 2;
// count = 'hi'; // 不可以，count 已经是 int
```

### `final`

变量只能赋值一次。

```dart
final name = 'Tom';
final now = DateTime.now();
```

特点：

- 运行时确定值也可以
- 赋值后不能再改

```dart
final name = 'Tom';
// name = 'Jack'; // 不可以
```

### `const`

编译期常量。

```dart
const appName = 'Demo';
const pi = 3.14;
```

特点：

- 值必须在编译时就确定
- 不能依赖运行时结果

```dart
// const now = DateTime.now(); // 不可以
```

### 一句话记忆

- `var`：普通变量，自动推断类型
- `final`：只能赋值一次
- `const`：编译期常量

<a id="toc-04"></a>
## 4. 基础类型 · [查看补充](chapters/04-basic-types.md)

```dart
String name = 'Tom';
int age = 18;
double price = 9.9;
bool isLogin = true;
```

也可以写成：

```dart
var name = 'Tom';
var age = 18;
var price = 9.9;
var isLogin = true;
```

<a id="toc-05"></a>
## 5. 字符串插值 · [查看补充](chapters/05-strings.md)

```dart
var name = 'Tom';
var age = 18;

print('name: $name');
print('next year: ${age + 1}');
```

规则：

- 简单变量：`$name`
- 表达式：`${...}`

<a id="toc-06"></a>
## 6. 条件判断 · [查看补充](chapters/06-conditions.md)

```dart
var score = 80;

if (score >= 90) {
  print('A');
} else if (score >= 60) {
  print('B');
} else {
  print('C');
}
```

<a id="toc-07"></a>
## 7. 循环 · [查看补充](chapters/07-loops.md)

```dart
for (var i = 0; i < 3; i++) {
  print(i);
}
```

```dart
var list = ['a', 'b', 'c'];

for (final item in list) {
  print(item);
}
```

```dart
var n = 0;
while (n < 3) {
  print(n);
  n++;
}
```

<a id="toc-08"></a>
## 8. 集合：List、Map、Set · [查看补充](chapters/08-collections.md)

### List

有序集合。

```dart
var numbers = [1, 2, 3];
numbers.add(4);

print(numbers[0]);
print(numbers.length);
```

明确类型：

```dart
List<int> numbers = [1, 2, 3];
```

### Map

键值对集合。

```dart
var user = {
  'name': 'Tom',
  'age': 18,
};

print(user['name']);
```

明确类型：

```dart
Map<String, dynamic> user = {
  'name': 'Tom',
  'age': 18,
};
```

### Set

不允许重复元素。

```dart
var ids = {1, 2, 3};
ids.add(3);

print(ids);
```

<a id="toc-09"></a>
## 9. 函数 · [查看补充](chapters/09-functions.md)

```dart
int add(int a, int b) {
  return a + b;
}
```

调用：

```dart
var result = add(1, 2);
print(result);
```

箭头函数：

```dart
int add(int a, int b) => a + b;
```

<a id="toc-10"></a>
## 10. 参数：位置参数、命名参数 · [查看补充](chapters/10-parameters.md)

### 位置可选参数

```dart
void greet([String? name]) {
  print('hello ${name ?? 'guest'}');
}
```

### 命名参数

```dart
void createUser({required String name, int age = 18}) {
  print('$name - $age');
}

createUser(name: 'Tom');
createUser(name: 'Jack', age: 20);
```

记住：

- Flutter 中命名参数非常常见
- `required` 表示必须传

<a id="toc-11"></a>
## 11. 空安全 · [查看补充](chapters/11-null-safety.md)

Dart 默认开启空安全。

### 非空类型

```dart
String name = 'Tom';
```

### 可空类型

```dart
String? name;
```

### 常用空安全操作符

```dart
String? name;

print(name?.length);
print(name ?? 'default');
```

说明：

- `?.`：为空时不继续访问
- `??`：左边为空时使用默认值

### 强制非空

```dart
String? name = 'Tom';
print(name!.length);
```

说明：

- `!` 表示“我确定这里不是 null”
- 如果判断错了，运行时会报错

<a id="toc-12"></a>
## 12. 类和对象 · [查看补充](chapters/12-classes.md)

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

使用：

```dart
final user = User('Tom', 18);
user.sayHello();
```

<a id="toc-13"></a>
## 13. 命名构造参数 · [查看补充](chapters/13-named-constructors.md)

Flutter 里很常见。

```dart
class User {
  final String name;
  final int age;

  User({required this.name, required this.age});
}
```

调用：

```dart
final user = User(name: 'Tom', age: 18);
```

<a id="toc-14"></a>
## 14. getter · [查看补充](chapters/14-getters.md)

```dart
class User {
  String firstName;
  String lastName;

  User(this.firstName, this.lastName);

  String get fullName => '$firstName $lastName';
}
```

使用：

```dart
final user = User('Tom', 'Lee');
print(user.fullName);
```

<a id="toc-15"></a>
## 15. 继承与重写 · [查看补充](chapters/15-inheritance.md)

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

<a id="toc-16"></a>
## 16. 异步：Future、async、await · [查看补充](chapters/16-async-await.md)

```dart
Future<String> fetchName() async {
  await Future.delayed(const Duration(seconds: 1));
  return 'Tom';
}
```

调用：

```dart
void main() async {
  final name = await fetchName();
  print(name);
}
```

理解：

- `Future<T>`：未来会得到一个 `T`
- `async`：函数内部可以使用 `await`
- `await`：等待异步结果

<a id="toc-17"></a>
## 17. 异常处理 · [查看补充](chapters/17-exceptions.md)

```dart
try {
  var result = 10 ~/ 0;
  print(result);
} catch (e, stackTrace) {
  print('error: $e');
}
```

<a id="toc-18"></a>
## 18. import · [查看补充](chapters/18-imports.md)

```dart
import 'dart:math';
import 'package:flutter/material.dart';
import 'app/app.dart';
```

作用：

- 把其他库或文件的内容引进来使用

起别名：

```dart
import 'app/app.dart' as app;

void main() {
  runApp(const app.HomeApp());
}
```

<a id="toc-19"></a>
## 19. Flutter 中最常见的 Dart 代码 · [查看补充](chapters/19-flutter-dart.md)

### 例子 1

```dart
runApp(const HomeApp());
```

包含：

- 函数调用
- 常量对象
- 类实例化

### 例子 2

```dart
MaterialApp(
  title: 'Home',
  debugShowCheckedModeBanner: false,
  onGenerateRoute: AppRouter.onGenerateRoute,
)
```

包含：

- 构造函数调用
- 命名参数
- 静态成员引用

### 例子 3

```dart
static const home = '/';
```

包含：

- `static`：属于类本身
- `const`：编译期常量

<a id="toc-20"></a>
## 20. print、debugPrint、log 的区别 · [查看补充](chapters/20-logging.md)

### `print`

- Dart 自带
- 最基础输出
- 不推荐长期保留在生产代码里

### `debugPrint`

- Flutter 常用调试输出
- 更适合开发阶段排查问题

```dart
debugPrint('route: ${settings.name}');
```

### `log`

- 更正式、结构化
- 适合模块化日志和错误记录

<a id="toc-21"></a>
## 21. 初学者常见坑 · [查看补充](chapters/21-common-pitfalls.md)

- 把 `var` 当成动态类型
- 分不清 `final` 和 `const`
- 忘了空安全
- 滥用 `!`
- 以为 `final List` 不能改内容

例如：

```dart
final list = [1, 2];
list.add(3); // 可以
```

原因：

- `final` 限制的是变量重新赋值
- 不一定限制对象内部内容变化

<a id="toc-22"></a>
## 22. 推荐书写习惯 · [查看补充](chapters/22-style-guide.md)

- 局部变量类型明显时用 `var`
- 默认优先考虑 `final`
- 能 `const` 就 `const`
- 少用 `dynamic`
- 空值优先用 `?.`、`??`
- Flutter 调试优先用 `debugPrint`

<a id="toc-23"></a>
## 23. 学习路线 · [查看补充](chapters/23-learning-path.md)

建议按这个顺序学：

1. 变量、基础类型、字符串
2. if / for / List / Map
3. 函数、命名参数
4. 类、构造函数
5. `var` / `final` / `const`
6. 空安全
7. 异步
8. 再回来看 Flutter 项目

<a id="toc-24"></a>
## 24. 10 个高频例子 · [查看补充](chapters/24-high-frequency-examples.md)

```dart
var name = 'Tom';
```

```dart
final now = DateTime.now();
```

```dart
const appName = 'Demo';
```

```dart
String? nickname;
```

```dart
print('hello $name');
```

```dart
int add(int a, int b) => a + b;
```

```dart
final list = [1, 2, 3];
```

```dart
final user = {'name': 'Tom', 'age': 18};
```

```dart
class User {
  final String name;
  User(this.name);
}
```

```dart
Future<void> load() async {
  await Future.delayed(const Duration(seconds: 1));
}
```

<a id="toc-25"></a>
## 25. 一页速记 · [查看补充](chapters/25-cheatsheet.md)

- `var`：自动推断类型
- `final`：只能赋值一次
- `const`：编译期常量
- `String?`：可空
- `?.`：安全访问
- `??`：空值兜底
- `!`：强制非空
- `[]`：List
- `{}`：Map 或 Set
- `async/await`：异步
- `required`：命名参数必传
- `static`：类成员

<a id="toc-26"></a>
## 26. 下一步怎么学 · [查看补充](chapters/26-next-steps.md)

如果你已经能看懂这份文档，下一步建议：

1. 对照 `lib/main.dart` 看入口函数和 import
2. 对照 `lib/app/app.dart` 看 `MaterialApp` 和命名参数
3. 对照 `lib/app/router/app_router.dart` 看类、静态方法、字符串插值、`switch`
4. 自己写一个 `User` 类、一个 `List`、一个 `Future` 练习
