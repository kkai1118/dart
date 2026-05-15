# 17 补充：异常处理

对应主文档章节：`17. 异常处理`

## 基本结构

```dart
try {
  doSomething();
} catch (e, stackTrace) {
  print('error: $e');
}
```

可以先这样理解：

- `try`：先尝试执行
- `catch`：如果出错，就到这里处理
- `finally`：不管有没有出错，最后都执行

## 最常见的完整结构

```dart
try {
  doSomething();
} catch (e, stackTrace) {
  print('error: $e');
} finally {
  print('done');
}
```

## 三个部分分别做什么

- `try`：放可能出错的代码
- `catch`：捕获错误对象
- `stackTrace`：错误调用栈，便于定位问题

## `on` 和 `catch` 的区别

### 只关心错误类型时，用 `on`

```dart
try {
  parseData();
} on FormatException {
  print('format error');
}
```

### 想拿到具体错误对象时，用 `catch`

```dart
try {
  parseData();
} catch (e) {
  print(e);
}
```

### 也可以一起用

```dart
try {
  parseData();
} on FormatException catch (e) {
  print('format error: $e');
}
```

可以这样记：

- `on`：先筛错误类型
- `catch`：拿到错误对象

## `stackTrace` 为什么有用

```dart
try {
  doSomething();
} catch (e, stackTrace) {
  print(stackTrace);
}
```

它能告诉你：

- 错误从哪一层调用过来的
- 大概是在哪个函数、哪一行附近出的问题

排查线上问题时很有价值。

## 可选的 `finally`

```dart
try {
  open();
} finally {
  close();
}
```

即使出错，`finally` 里的清理逻辑也会执行。

常见场景：

- 关闭文件
- 释放资源
- 收尾打印日志

## `rethrow` 是什么

有时候你想先记录一下错误，再把它继续抛出去。

```dart
try {
  fetchData();
} catch (e) {
  print('log error: $e');
  rethrow;
}
```

`rethrow` 的意思是：

- 这里先做一层处理
- 但不把错误吃掉
- 继续交给上层去处理

## 同步异常和异步异常

### 同步异常

```dart
try {
  var result = 10 ~/ 0;
  print(result);
} catch (e) {
  print(e);
}
```

### 异步异常

```dart
try {
  final data = await fetchData();
  print(data);
} catch (e) {
  print(e);
}
```

在异步代码里，通常也要配合 `await` 才能在当前 `try/catch` 中接住异常。

## 什么时候不该把异常吞掉

不推荐这样：

```dart
try {
  fetchData();
} catch (e) {}
```

因为这样做的问题是：

- 错误发生了
- 但没有日志
- 也没有继续抛出
- 后面排查会非常困难

更推荐至少做一件事：

- 打日志
- 给用户提示
- 或者 `rethrow`

## 实战建议

- 不要吞掉异常后什么都不做
- 至少记录日志，保留定位信息
- 对用户可见的失败场景，给出明确提示

## Flutter 场景

在 Flutter 里，异常处理经常出现在这些地方：

- 网络请求失败
- JSON 解析失败
- 本地缓存读取失败
- 页面初始化失败

这时通常要同时考虑两件事：

- 开发者怎么定位问题
- 用户界面怎么给出合理反馈
