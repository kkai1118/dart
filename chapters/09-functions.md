# 09 补充：函数

对应主文档章节：`9. 函数`

## 函数的基本组成

```dart
int add(int a, int b) {
  return a + b;
}
```

拆开看：

- `int`：返回值类型
- `add`：函数名
- `(int a, int b)`：参数列表
- `return`：返回结果

## 无返回值函数

```dart
void logMessage(String message) {
  print(message);
}
```

## 箭头函数什么时候用

只有一条返回语句时最适合。

```dart
int add(int a, int b) => a + b;
```

## 函数也是对象

Dart 里函数可以赋值给变量、作为参数传递，这也是 Flutter 回调很多的原因。
