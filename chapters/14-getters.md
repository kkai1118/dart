# 14 补充：getter

对应主文档章节：`14. getter`

## getter 是什么

getter 让你像访问字段一样访问一个计算结果。

```dart
class User {
  String firstName;
  String lastName;

  User(this.firstName, this.lastName);

  String get fullName => '$firstName $lastName';
}
```

调用时：

```dart
print(user.fullName);
```

不是：

```dart
print(user.fullName());
```

## 适合放进 getter 的逻辑

- 轻量计算
- 格式化展示字段
- 对多个字段做简单组合

## 不适合放进 getter 的逻辑

- 网络请求
- 重计算
- 有副作用的代码
