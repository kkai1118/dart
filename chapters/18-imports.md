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

### 1. `dart:`

导入 Dart 自带的标准库。

```dart
import 'dart:math';
import 'dart:convert';
```

常见用途：

- `dart:math`：数学相关
- `dart:convert`：JSON、编码解码

### 2. `package:`

导入项目依赖或框架提供的包。

```dart
import 'package:flutter/material.dart';
```

这类写法在 Flutter 项目里非常常见。

### 3. 相对路径

导入当前项目里的其他文件。

```dart
import 'app/app.dart';
import '../models/user.dart';
```

适合项目内部文件之间互相引用。

## 导入后能做什么

导入之后，当前文件才能使用对应文件里的类、函数、常量等公开内容。

比如：

```dart
import 'dart:math';

void main() {
  print(max(1, 3));
}
```

如果没有 `import 'dart:math';`，这里通常就不能直接用 `max(...)`。

## 什么时候起别名

```dart
import 'app/app.dart' as app;
```

适合场景：

- 名称可能冲突
- 想让来源更显式
- 导入的是大模块

使用时：

```dart
app.HomeApp()
```

这样读代码时会更清楚：`HomeApp` 是从 `app` 这个库里来的。

## 还可以限制导入范围

```dart
import 'app/app.dart' show HomeApp;
```

这种写法有助于增强可读性。

## `show` 和 `hide`

### `show`

只导入指定内容：

```dart
import 'app/app.dart' show HomeApp;
```

意思是：只把 `HomeApp` 导进来。

### `hide`

排除某些内容：

```dart
import 'app/app.dart' hide HomeApp;
```

意思是：导入这个文件的大部分公开内容，但不要 `HomeApp`。

## Dart 自带标准库总览

下面按平台把常见的 `dart:*` 标准库整理一下。初学时不用全背，先知道“遇到什么问题大概该去哪个库找”就够了。

## 多平台都能用

### `dart:core`

- 最基础的核心库
- 包含字符串、数字、布尔、`List`、`Map`、`Set`、异常、`DateTime`、`Uri` 等
- 每个 Dart 程序都会自动导入它

### `dart:async`

- 异步编程相关
- 重点有 `Future`、`Stream`、`Timer`、`Zone`

### `dart:collection`

- 对集合能力的补充
- 常见于更丰富的集合类型和工具类

### `dart:convert`

- 编码和解码
- 常见于 JSON、UTF-8 等数据转换

### `dart:developer`

- 开发调试相关
- 用于和调试器、开发工具交互

### `dart:math`

- 数学计算相关
- 常见于 `min`、`max`、随机数、三角函数、常量等

### `dart:typed_data`

- 高效处理固定类型数据
- 常见于字节数据、二进制数据、`Uint8List` 等

## Dart Native 平台可用

这类库主要用于 Dart VM、命令行、服务端、Flutter 原生运行环境。

### `dart:ffi`

- C 语言互操作
- 让 Dart 调用原生 C API

### `dart:io`

- 文件、目录、Socket、HTTP、进程、标准输入输出等 I/O 能力
- Flutter、服务端、命令行开发里都很常见

### `dart:isolate`

- 并发编程
- 用于创建隔离区（isolate）处理独立任务

### `dart:mirrors`

- 反射
- 可以做运行时查看和动态调用
- 属于实验性能力，而且 Flutter 不支持它

## Web 平台相关

### `dart:js_interop`

- 新的 JavaScript 互操作方式
- 用于和 JS 及浏览器能力交互

### `dart:js_interop_unsafe`

- 更底层地动态操作 JavaScript 对象
- 适合一些更灵活但更需要小心的 JS 互操作场景

## Web 旧版库（Legacy）

这些库仍然存在，但官方更推荐用 `dart:js_interop` 配合 `package:web`。

### `dart:html`

- 浏览器 HTML 和 DOM 操作
- 旧版 Web 开发里非常常见

### `dart:indexed_db`

- 浏览器端 IndexedDB 本地存储
- 适合客户端键值数据存储

### `dart:js`

- 较旧的 JavaScript 互操作方式
- 现在更推荐 `dart:js_interop`

### `dart:js_util`

- 较旧的 JS 工具方法库
- 现在很多场景由 `dart:js_interop_unsafe` 替代

### `dart:svg`

- 浏览器中的 SVG 图形能力
- 用于二维矢量图形

### `dart:web_audio`

- 浏览器音频处理
- 用于高保真 Web 音频编程

### `dart:web_gl`

- 浏览器 3D 图形能力
- 用于 WebGL 相关场景

## 初学者最常接触的几个库

如果你现在主要学 Dart / Flutter，优先熟悉这些就够了：

- `dart:core`
- `dart:async`
- `dart:convert`
- `dart:math`
- `dart:io`
- `dart:typed_data`

## 一个很实用的记法

- 写基础语法时，很多能力其实来自 `dart:core`
- 做异步时，先想到 `dart:async`
- 处理 JSON 时，先想到 `dart:convert`
- 做计算时，先想到 `dart:math`
- 操作文件和网络时，先想到 `dart:io`
- 做 Web 和 JS 互操作时，先想到 `dart:js_interop`

## 为什么 Flutter 项目里 `import` 很多

因为一个页面通常会依赖很多东西：

- Flutter 自带组件
- 项目里的公共组件
- 路由文件
- 数据模型
- 工具函数

所以你经常会在文件开头看到一串 `import`。

## 读 `import` 时怎么快速判断

- 看到 `dart:`：先想这是 Dart 自带库
- 看到 `package:flutter/...`：先想这是 Flutter 框架内容
- 看到 `package:你的项目名/...` 或相对路径：先想这是项目自己的代码

## 实战建议

- 用到什么再导入什么
- 名称冲突时优先考虑别名
- 文件很大、公开内容很多时，可以考虑 `show`
- 读项目代码时，先扫一眼 `import`，能快速知道这个文件依赖了哪些模块
