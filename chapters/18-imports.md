# 18 补充：import

对应主文档章节：`18. import`

## import 的作用

把其他文件或库中的公开内容引入当前文件。

```dart
import 'dart:math';
import 'package:flutter/material.dart';
import 'app/app.dart';
```

## 三类常见来源

- `dart:`：Dart 内置库
- `package:`：包或框架库
- 相对路径：项目内部文件

## 什么时候起别名

```dart
import 'app/app.dart' as app;
```

适合场景：

- 名称可能冲突
- 想让来源更显式
- 导入的是大模块

## 还可以限制导入范围

```dart
import 'app/app.dart' show HomeApp;
```

这种写法有助于增强可读性。
