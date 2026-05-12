# 11 补充：空安全

对应主文档章节：`11. 空安全`

## 先建立一个核心意识

`String` 和 `String?` 是两种不同类型。

```dart
String name = 'Tom';
String? nickname;
```

## 四个高频操作符

### `?`

声明可空类型：

```dart
String? name;
```

### `?.`

安全访问：

```dart
print(name?.length);
```

### `??`

空值兜底：

```dart
print(name ?? 'guest');
```

### `!`

强制非空：

```dart
print(name!.length);
```

## 最实用建议

- 优先用 `?.` 和 `??`
- 少用 `!`
- 如果编译器提示你可能为空，优先思考数据流而不是强压过去
