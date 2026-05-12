# 19 补充：Flutter 中最常见的 Dart 代码

对应主文档章节：`19. Flutter 中最常见的 Dart 代码`

## 看 Flutter 代码的建议顺序

看到一段 UI 代码时，优先按下面顺序读：

1. 这是在创建哪个类的实例
2. 传了哪些命名参数
3. 哪些参数是回调函数
4. 哪些地方用了 `const`

## 典型例子

```dart
MaterialApp(
  title: 'Home',
  onGenerateRoute: AppRouter.onGenerateRoute,
)
```

拆开看：

- `MaterialApp`：创建一个对象
- `title:`：命名参数
- `AppRouter.onGenerateRoute`：把静态方法作为参数传进去

## 为什么 Flutter 代码看起来像“函数嵌套函数”

本质上很多地方是在连续创建对象，只是写成树状结构。
