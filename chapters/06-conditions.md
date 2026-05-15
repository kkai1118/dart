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

适合场景：

- 条件很简单
- 只是二选一结果
- 想写得更紧凑一些

如果逻辑已经比较复杂，还是更推荐普通 `if/else`。

## `switch` 基础

当你要根据“一个值的不同情况”做不同分支时，`switch` 也很常见。

```dart
var role = 'admin';

switch (role) {
  case 'admin':
    print('管理员');
    break;
  case 'guest':
    print('游客');
    break;
  default:
    print('普通用户');
}
```

可以先这样理解：

- `switch`：看某个值是多少
- `case`：不同情况分别怎么处理
- `default`：都不匹配时走这里

## 条件判断和空安全一起用

真实代码里，你经常会同时遇到条件判断和可空值。

```dart
String? name;

if (name != null) {
  print(name.length);
}
```

这段代码的意思是：

- 先判断 `name` 不是 `null`
- 再安全地去访问它

有时候也会写成：

```dart
var text = name ?? 'guest';
print(text);
```

这种写法更适合“为空就给默认值”的场景。

## Flutter 常见用法

- 控制是否展示某个 Widget
- 根据状态选择不同文案或颜色
- 按权限、登录态分支逻辑
