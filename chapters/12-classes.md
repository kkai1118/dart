# 12 补充：类和对象

对应主文档章节：`12. 类和对象`

## 为什么 Flutter 代码里到处都是类

Flutter 的页面、组件、配置对象、模型对象，本质上大量都通过类表达。

## 类的三个常见组成部分

```dart
class User {
  String name;
  int age;

  User(this.name, this.age);

  void sayHello() {
    print('hello, I am $name');
  }
}
```

- 字段：`name`、`age`
- 构造函数：`User(...)`
- 方法：`sayHello()`

## `this.name` 是什么

表示“把传进来的参数赋值给当前对象的字段”。

## 读代码技巧

看到 `SomeClass(...)` 时，优先判断它是不是在创建对象实例。
