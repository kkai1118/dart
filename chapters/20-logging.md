# 20 补充：`print`、`debugPrint`、`log`

对应主文档章节：`20. print、debugPrint、log 的区别`

## 一句话区分

- `print`：最基础输出
- `debugPrint`：Flutter 调试输出
- `log`：更结构化的日志 API

## `print`

`print` 是 Dart 自带的最基础输出方式。

```dart
print('hello');
print(123);
print({'name': 'Tom'});
```

特点：

- 写法最简单
- 几乎什么时候都能先用一下
- 可以直接打印字符串、数字、对象

适合场景：

- 学习语法时临时看结果
- 快速确认某个变量值
- 命令行小程序里的简单输出

局限：

- 信息比较“裸”
- 不带级别、分类、模块信息
- 项目大了之后，不方便统一管理

## `debugPrint`

`debugPrint` 是 Flutter 里很常见的调试输出方式。

```dart
debugPrint('route: /home');
debugPrint('count: $count');
```

特点：

- 更偏 Flutter 调试场景
- 常用于页面、路由、状态变化排查
- 一般比随手乱写 `print` 更符合 Flutter 项目习惯

参数类型注意：

```dart
debugPrint('hello'); // 可以
// debugPrint(123); // 不可以
```

因为它接收的是 `String?`，所以通常要自己转成字符串：

```dart
debugPrint('$count');
```

## `log`

`log` 来自 `dart:developer`，更适合写结构化日志。

```dart
import 'dart:developer';

log('request success', name: 'network');
```

特点：

- 比 `print` 更正式
- 可以带日志分类名
- 更适合模块化、可筛选的日志

常见写法：

```dart
log(
  'login failed',
  name: 'auth',
  error: e,
  stackTrace: stackTrace,
);
```

适合场景：

- 记录模块级日志
- 配合错误信息一起输出
- 需要更清晰地区分来源时

## 三者放在一起看

### `print`

- 最简单
- 最随手
- 更适合临时输出

### `debugPrint`

- 更偏 Flutter 调试
- 更适合页面和交互排查
- 参数一般要是字符串

### `log`

- 更结构化
- 更适合正式日志
- 能带模块名、错误信息、堆栈信息

## 一个直观例子

### 用 `print`

```dart
print('user loaded');
```

### 用 `debugPrint`

```dart
debugPrint('route: ${settings.name}');
```

### 用 `log`

```dart
log('request failed', name: 'network', error: e);
```

## 在 Flutter 项目里怎么选

如果你只是：

- 临时看一个值
- 看按钮点没点到
- 看页面有没有刷新

优先用：

```dart
debugPrint('count: $count');
```

如果你是：

- 想保留更正式的日志
- 想区分网络、登录、路由等模块
- 想一起记录错误和堆栈

优先考虑：

```dart
log('request failed', name: 'network', error: e, stackTrace: stackTrace);
```

## 一个实用习惯

不管你用哪种方式，尽量不要只打印模糊信息。

比如不推荐：

```dart
debugPrint('here');
```

更推荐：

```dart
debugPrint('login page submit clicked, phone: $phone');
```

这样回头看日志时，你才能快速知道：

- 是哪个页面
- 是哪个动作
- 关键变量是什么

## 参数类型差异

```dart
print(123); // 可以
```

```dart
// debugPrint(123); // 不可以
```

因为 `debugPrint` 接收的是 `String?`，而不是任意对象。

## 当前项目里该怎么选

- 临时调试页面和路由：`debugPrint`
- 正式日志体系：再考虑 `log` 或日志框架
- 不建议在生产代码里长期保留大量 `print`
