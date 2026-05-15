# 10 补充：参数

对应主文档章节：`10. 参数：位置参数、命名参数`

## 三类参数

- 必填位置参数
- 可选位置参数：`[]`
- 可选命名参数：`{}`

先记一个总规则：

- 写在 `()` 里的普通参数，通常按顺序传
- 写在 `[]` 里的，是可选位置参数
- 写在 `{}` 里的，是命名参数

## 1. 必填位置参数

这是最基础、最常见的一类参数。

```dart
int add(int a, int b) {
  return a + b;
}
```

调用时：

```dart
add(1, 2);
```

特点：

- 必须传
- 按顺序传
- 少一个不行，多一个也不行

### 为什么叫“位置参数”

因为它不看名字，主要看位置。

```dart
void printUser(String name, int age) {
  print('$name - $age');
}

printUser('Tom', 18);
```

这里：

- 第 1 个位置给 `name`
- 第 2 个位置给 `age`

如果顺序反了，含义就变了，甚至会直接报错。

## 2. 可选位置参数 `[]`

这类参数可以传，也可以不传。

```dart
void greet([String? name]) {
  print('hello ${name ?? 'guest'}');
}
```

调用时：

```dart
greet();
greet('Tom');
```

特点：

- 不一定要传
- 还是按位置传
- 不传时，通常是 `null`，或者使用默认值

### 可选位置参数的默认值

```dart
void greet([String name = 'guest']) {
  print('hello $name');
}
```

调用时：

```dart
greet(); // hello guest
greet('Tom'); // hello Tom
```

### 多个可选位置参数

```dart
void showUser(String name, [int age = 18, String city = 'Shanghai']) {
  print('$name - $age - $city');
}
```

调用时：

```dart
showUser('Tom');
showUser('Tom', 20);
showUser('Tom', 20, 'Beijing');
```

说明：

- 第 1 个参数 `name` 是必填位置参数
- 后面的 `age`、`city` 是可选位置参数
- 可选位置参数还是按顺序传，不能跳着传

比如这个不行：

```dart
// showUser('Tom', 'Beijing'); // 不可以，第二个位置应该是 int age
```

### 适合什么场景

- 参数不多
- 顺序很自然
- 少传几个也不影响理解

比如：

```dart
void showMessage(String title, [String subtitle = '']) {
  print('$title - $subtitle');
}
```

## 3. 可选命名参数 `{}`

这类参数最适合“参数比较多，或者调用时希望更清楚”。

```dart
void createUser({String? name, int age = 18}) {
  print('$name - $age');
}
```

调用时：

```dart
createUser();
createUser(name: 'Tom');
createUser(name: 'Jack', age: 20);
```

特点：

- 参数名要写出来
- 顺序通常不重要
- 可读性更强

### `required` 的作用

有些命名参数虽然写在 `{}` 里，但仍然要求必须传。

```dart
void createUser({required String name, int age = 18}) {
  print('$name - $age');
}
```

调用时：

```dart
createUser(name: 'Tom');
```

这里：

- `name` 必须传
- `age` 可以不传

### 为什么 Flutter 大量使用命名参数

```dart
Container(
  width: 100,
  height: 40,
  color: Colors.blue,
)
```

优点：

- 调用处更易读
- 参数多时不容易传错顺序
- 适合 UI 构造函数

因为像 Flutter 组件这种场景，经常有很多配置项：

- 宽高
- 颜色
- 内边距
- 点击事件
- 子组件

如果全用位置参数，可读性会很差。

## 三类参数放在一起看

```dart
void demo(
  String title,
  [String subtitle = ''],
  {bool visible = true},
) {
  print('$title - $subtitle - $visible');
}
```

调用时：

```dart
demo('Home');
demo('Home', 'Welcome');
demo('Home', 'Welcome', visible: false);
```

这个例子可以帮你一起记住：

- `title`：必填位置参数
- `subtitle`：可选位置参数
- `visible`：可选命名参数

## 初学者最容易混淆的点

### 1. `[]` 和 `{}` 不一样

- `[]`：还是按位置传
- `{}`：按名字传

### 2. 命名参数不一定都是可省略

加了 `required` 之后，就必须传。

### 3. 参数越多，越适合命名参数

尤其在 Flutter 里，只要你看到这种写法：

```dart
Text(
  'Hello',
  maxLines: 2,
  overflow: TextOverflow.ellipsis,
)
```

通常就是“第一个是位置参数，后面很多是命名参数”。

## 读代码技巧

- 看到 `xxx: yyy` 时，先判断：这通常是在传命名参数
- 看到 `[]`，要想到“可选位置参数”
- 看到函数调用里只写值、不写参数名，通常是在传位置参数
