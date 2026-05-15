# 04 补充：基础类型

对应主文档章节：`4. 基础类型`

## 最常见的五类

```dart
String name = 'Tom';
int age = 18;
double price = 9.9;
bool isLogin = true;
Object anything = 'hello';
```

## `int` 和 `double`

- `int`：整数，比如 `1`、`42`
- `double`：浮点数，比如 `3.14`、`9.9`

```dart
var a = 1;
var b = 1.0;
```

这里 `a` 是 `int`，`b` 是 `double`。

## `Object`、`dynamic`、`Object?`

- `Object`：任意非空对象
- `Object?`：任意对象，允许 `null`
- `dynamic`：关闭静态类型检查，谨慎使用

这里的“非空”重点是：不能是 `null`，不是说内容不能空。

比如这些都可以赋值给 `Object`：

```dart
Object a = '';
Object b = [];
Object c = {};
Object d = 0;
```

因为它们虽然可能“内容为空”，但它们本身都不是 `null`。

## `NaN`、`null`、`Object`、`dynamic` 的区别

这几个词初学时很容易混在一起，但它们其实不是一类概念。

### `NaN`

`NaN` 是 `Not a Number`，表示“不是一个正常数字结果”。

```dart
var x = 0.0 / 0.0;
print(x); // NaN
```

- `NaN` 属于 `double`
- 它不是 `null`
- 它是一个真实存在的值，只是这个值比较特殊

### `null`

`null` 表示“没有值”。

```dart
String? name = null;
```

- `null` 不是字符串、不是数字
- 它表示变量当前没有实际内容
- 在空安全下，只有可空类型才能接收 `null`

### `Object`

`Object` 可以接收几乎所有非 `null` 的值。

```dart
Object a = 123;
Object b = 'hello';
Object c = false;
```

但这个不行：

```dart
// Object x = null; // 不可以
```

如果想接收 `null`，要写成：

```dart
Object? x = null;
```

### `dynamic`

`dynamic` 表示：先不要做严格静态类型检查。

```dart
dynamic value = 'hello';
value = 123;
value = null;
```

特点：

- 可以接收各种类型
- 编译器对它的约束更少
- 写起来方便，但更容易把错误拖到运行时

## 一句话区分

- `NaN`：特殊的 `double`
- `null`：没有值
- `Object`：几乎任何非 `null` 值都可以接
- `dynamic`：类型检查放宽，使用时要更小心

## 实战建议

- 业务字段能写具体类型就写具体类型
- 少用 `dynamic`
- 读不清类型时，先看变量初始值和函数返回值
