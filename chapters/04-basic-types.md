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

## 实战建议

- 业务字段能写具体类型就写具体类型
- 少用 `dynamic`
- 读不清类型时，先看变量初始值和函数返回值
