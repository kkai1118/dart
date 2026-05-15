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

可以先这样理解：

- 字段：直接保存的数据
- getter：每次访问时现算一个结果，但写法看起来像字段

## getter 和普通方法的区别

### getter

```dart
print(user.fullName);
```

### 普通方法

```dart
print(user.fullName());
```

区别在于：

- getter 访问时不写 `()`
- 方法调用时要写 `()`

如果一个逻辑更像“读取一个属性”，getter 往往更自然。

## 为什么要用 getter

因为有些结果不是直接存着的，而是根据现有字段计算出来的。

比如：

```dart
class User {
  String firstName;
  String lastName;

  User(this.firstName, this.lastName);

  String get fullName => '$firstName $lastName';
}
```

这里 `fullName` 没有单独存起来，而是根据 `firstName` 和 `lastName` 组合出来的。

## getter 常见例子

### 拼接展示字段

```dart
String get fullName => '$firstName $lastName';
```

### 计算布尔状态

```dart
bool get isAdult => age >= 18;
```

### 生成格式化文案

```dart
String get displayText => '$name ($age)';
```

## 适合放进 getter 的逻辑

- 轻量计算
- 格式化展示字段
- 对多个字段做简单组合

## 不适合放进 getter 的逻辑

- 网络请求
- 重计算
- 有副作用的代码

原因是：getter 看起来像“读一个属性”，调用者通常会默认它很轻、很快、很安全。

## setter 先顺手认识一下

和 getter 对应的，还有 setter。

```dart
class User {
  String _name = '';

  String get name => _name;

  set name(String value) {
    _name = value.trim();
  }
}
```

使用时：

```dart
user.name = ' Tom ';
print(user.name);
```

初学阶段不用深挖，只要知道：

- getter：读取
- setter：写入时做控制

## 读代码技巧

- 看到 `get xxx => ...`，说明这是 getter
- 看到 `user.xxx` 但这个值并不是字段声明出来的，可能就是 getter
- 如果逻辑只是“轻量计算结果”，getter 往往比方法更自然
