# 02 补充：第一个 Dart 程序

对应主文档章节：`2. 第一个 Dart 程序`

## 逐行理解

```dart
void main() {
  print('Hello Dart');
}
```

- `main` 是程序入口，Dart 程序从这里开始执行
- `()` 里是参数列表，这里为空
- `{}` 是函数体
- 每条语句通常以 `;` 结尾

## main 一定要写成这样吗

不一定，常见还有这些写法：

```dart
void main() => print('Hello Dart');
```

```dart
Future<void> main() async {
  await Future.delayed(const Duration(milliseconds: 100));
}
```

## 在 Flutter 里的对应关系

Flutter 项目通常是：

```dart
void main() {
  runApp(const HomeApp());
}
```

这里的差别只是把“打印一句话”换成了“启动整个应用”。
