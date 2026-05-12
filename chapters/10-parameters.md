# 10 补充：参数

对应主文档章节：`10. 参数：位置参数、命名参数`

## 三类参数

- 必填位置参数
- 可选位置参数：`[]`
- 可选命名参数：`{}`

## 为什么 Flutter 大量使用命名参数

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

## `required` 的作用

```dart
void createUser({required String name}) {}
```

表示：虽然是命名参数，但调用者必须传。

## 读代码技巧

看到大量 `xxx: yyy` 时，先判断：这通常是在传命名参数。
