# 24 补充：10 个高频例子

对应主文档章节：`24. 10 个高频例子`

## 怎么使用这些例子

不要只看，建议每个例子都自己改两次：

- 改变量名
- 改类型
- 改返回值
- 改成错误写法再看报错

## 1. 变量

```dart
var name = 'Tom';
final age = 18;
const appName = 'Demo';
```

## 2. 字符串插值

```dart
var name = 'Tom';
print('hello $name');
```

## 3. 条件判断

```dart
var score = 80;
if (score >= 60) {
  print('pass');
}
```

## 4. List

```dart
final list = [1, 2, 3];
list.add(4);
print(list[0]);
```

## 5. Map

```dart
final user = {
  'name': 'Tom',
  'age': 18,
};
print(user['name']);
```

## 6. 函数

```dart
int add(int a, int b) {
  return a + b;
}
```

## 7. 命名参数

```dart
void createUser({required String name, int age = 18}) {
  print('$name - $age');
}
```

## 8. 类和对象

```dart
class User {
  final String name;

  User(this.name);
}

final user = User('Tom');
```

## 9. 空安全

```dart
String? name;
print(name ?? 'guest');
```

## 10. 异步

```dart
Future<String> fetchName() async {
  return 'Tom';
}
```

## 一个示范：怎么把例子练透

原例子：

```dart
int add(int a, int b) => a + b;
```

你可以改成：

```dart
double add(double a, double b) => a + b;
```

再改成：

```dart
String add(String a, String b) => a + b;
```

这样你会更快理解“类型”和“函数签名”的关系。

## 怎么用这 10 个例子

建议这样练：

- 先照着敲一遍
- 再自己改变量名和类型
- 再故意写错一次，看报错提示
- 最后去 Flutter 项目里找对应写法
