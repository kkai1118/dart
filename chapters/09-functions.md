# 09 补充：函数

对应主文档章节：`9. 函数`

## 函数的基本组成

```dart
int add(int a, int b) {
  return a + b;
}
```

拆开看：

- `int`：返回值类型
- `add`：函数名
- `(int a, int b)`：参数列表
- `return`：返回结果

## 无返回值函数

```dart
void logMessage(String message) {
  print(message);
}
```

## 箭头函数什么时候用

只有一条返回语句时最适合。

```dart
int add(int a, int b) => a + b;
```

## 函数也是对象

Dart 里函数可以赋值给变量、作为参数传递，这也是 Flutter 回调很多的原因。

## 函数可以赋值给变量

```dart
int add(int a, int b) {
  return a + b;
}

var fn = add;
print(fn(1, 2)); // 3
```

这里的 `fn` 就是一个变量，但它保存的是函数。

## 函数可以作为参数传递

```dart
void runTwice(void Function() action) {
  action();
  action();
}

void sayHello() {
  print('hello');
}

runTwice(sayHello);
```

这里的 `sayHello` 被当成参数传给了 `runTwice`。

## 为什么 Flutter 里回调很多

因为 Flutter 组件经常需要“先把动作留给你决定”。

比如按钮点击：

```dart
ElevatedButton(
  onPressed: () {
    print('clicked');
  },
  child: const Text('提交'),
)
```

这里的 `onPressed` 就是在接收一个函数。

你可以把它理解成：

- 组件负责显示界面
- 你把“点了以后做什么”这个函数传进去

这就是为什么 Flutter 代码里经常会看到：

- `onPressed`
- `onTap`
- `onChanged`
- `itemBuilder`

它们本质上都是“把函数传进去”。
