# 16 补充：异步 `Future`、`async`、`await`

对应主文档章节：`16. 异步：Future、async、await`

## 先建立直觉

`Future<T>` 可以理解成：将来会拿到一个 `T`。

```dart
Future<String> fetchName() async {
  return 'Tom';
}
```

## 为什么需要 `await`

```dart
final name = await fetchName();
```

如果不用 `await`，你拿到的是 `Future<String>`，不是最终字符串。

## 两个常见错误

### 1. 在非 `async` 函数里用 `await`

```dart
// void main() {
//   await fetchName();
// }
```

### 2. 忘记处理异常

```dart
try {
  final data = await fetchData();
} catch (e) {
  print(e);
}
```

## Flutter 场景

- 网络请求
- 文件读写
- 延迟执行
- 初始化流程
