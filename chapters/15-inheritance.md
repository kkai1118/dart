# 15 补充：继承与重写

对应主文档章节：`15. 继承与重写`

## 基础关系

```dart
class Animal {
  void speak() {
    print('...');
  }
}

class Dog extends Animal {
  @override
  void speak() {
    print('wang');
  }
}
```

- `extends`：继承
- `@override`：重写父类方法

## 为什么要写 `@override`

- 让代码意图更清楚
- 编译器能帮你检查签名是否正确

## Flutter 中常见的“重写”

```dart
@override
Widget build(BuildContext context) {
  return Container();
}
```

这是你最常见的一种方法重写。
