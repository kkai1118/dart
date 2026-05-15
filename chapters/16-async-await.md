# 16 补充：异步 `Future`、`async`、`await`

对应主文档章节：`16. 异步：Future、async、await`

## 先建立直觉

`Future<T>` 可以理解成：将来会拿到一个 `T`。

```dart
Future<String> fetchName() async {
  return 'Tom';
}
```

这里：

- `Future<String>`：表示未来会得到一个 `String`
- 现在不一定立刻拿到结果
- 结果可能稍后才返回

## 同步和异步的区别

可以先这样理解：

- 同步：代码一行一行直接往下执行，当前这步没做完，后面先别走
- 异步：先把要等待的事情交出去，结果回来后再继续处理

比如：

```dart
print('A');
print('B');
print('C');
```

这是同步顺序执行。

而网络请求、磁盘读取、延迟等待这类事情，通常更适合异步处理。

## `async` 是做什么的

`async` 表示：这个函数内部可以使用 `await`。

```dart
Future<String> fetchName() async {
  return 'Tom';
}
```

它通常和 `Future` 一起出现。

你可以简单记：

- `Future`：说明结果会稍后到
- `async`：说明函数里可以等待异步结果
- `await`：说明这里要等一下结果

## 为什么需要 `await`

```dart
final name = await fetchName();
```

如果不用 `await`，你拿到的是 `Future<String>`，不是最终字符串。

对比一下：

```dart
final result = fetchName();
print(result); // Instance of 'Future<String>'
```

```dart
final name = await fetchName();
print(name); // Tom
```

所以 `await` 的作用不是“让函数变异步”，而是：

- 等待异步结果回来
- 拿到真正的值

## 一个完整例子

```dart
Future<String> fetchName() async {
  await Future.delayed(const Duration(seconds: 1));
  return 'Tom';
}

Future<void> main() async {
  print('start');
  final name = await fetchName();
  print(name);
  print('end');
}
```

执行顺序可以理解成：

1. 先打印 `start`
2. 等待 `fetchName()` 完成
3. 拿到返回值 `Tom`
4. 再继续往下打印 `end`

## `Future<void>` 是什么

有些异步函数不需要返回具体数据，只是要“异步做完一件事”。

```dart
Future<void> saveUser() async {
  await Future.delayed(const Duration(seconds: 1));
}
```

这里的意思是：

- 这是一个异步函数
- 将来会完成
- 但不会返回具体业务值

## 最常见的异步来源

- 网络请求
- 文件读写
- 数据库存取
- 延迟执行
- 初始化配置加载

## 两个常见写法

### 1. 等待一个结果

```dart
final user = await fetchUser();
```

### 2. 等待一段时间

```dart
await Future.delayed(const Duration(seconds: 1));
```

这在练习异步、模拟加载中状态时很常见。

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

## 初学者最容易混淆的点

### 1. `async` 不等于“立刻拿到结果”

加了 `async` 之后，函数通常返回的是 `Future`，不是最终值。

### 2. `await` 只能在 `async` 函数里用

如果函数没写 `async`，就不能直接写 `await`。

### 3. 异步代码不是“更快执行完”

异步的重点不是速度更快，而是：

- 等待期间不把主流程完全卡死
- 结果回来后再继续处理

## Flutter 场景里怎么理解

在 Flutter 里，异步通常对应这些事情：

- 打开页面后请求接口
- 读取本地缓存
- 提交表单
- 初始化用户信息
- 等待动画或延迟跳转

## Flutter 场景

- 网络请求
- 文件读写
- 延迟执行
- 初始化流程
