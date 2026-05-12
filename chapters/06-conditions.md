# 06 补充：条件判断

对应主文档章节：`6. 条件判断`

## 典型结构

```dart
if (score >= 90) {
  print('A');
} else if (score >= 60) {
  print('B');
} else {
  print('C');
}
```

## 条件必须是布尔值

Dart 不像某些语言那样把非空、非零自动当成真。

```dart
var ok = true;
if (ok) {
  print('yes');
}
```

## 三元表达式

简单条件可写成：

```dart
var label = isLogin ? '已登录' : '未登录';
```

## Flutter 常见用法

- 控制是否展示某个 Widget
- 根据状态选择不同文案或颜色
- 按权限、登录态分支逻辑
