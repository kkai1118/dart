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

作用：声明“这个变量允许是 `null`”。

```dart
String? name;
```

说明：

- `String` 表示必须是字符串，不能是 `null`
- `String?` 表示可以是字符串，也可以是 `null`

对比：

```dart
String name = 'Tom';
String? nickname = null;
```

这里：

- `name` 不能随便赋值成 `null`
- `nickname` 可以是 `null`

你可以把 `?` 理解成：“这个类型后面加了一个允许为空的标记”。

### `?.`

作用：安全访问。只有左边不是 `null` 时，才继续往后取值。

```dart
print(name?.length);
```

可以这样理解：

- 如果 `name` 有值，就取 `length`
- 如果 `name` 是 `null`，整个结果直接变成 `null`

它大致相当于：

```dart
print(name == null ? null : name.length);
```

例子：

```dart
String? name = 'Tom';
print(name?.length); // 3

name = null;
print(name?.length); // null
```

适合场景：

- 你不确定变量是不是 `null`
- 但你希望“如果为空就别继续报错”

### `??`

作用：空值兜底。左边如果是 `null`，就使用右边的默认值。

```dart
print(name ?? 'guest');
```

例子：

```dart
String? name = 'Tom';
print(name ?? 'guest'); // Tom

name = null;
print(name ?? 'guest'); // guest
```

可以这样理解：

- 有值就用原来的值
- 没值就用备用值

它大致相当于：

```dart
print(name == null ? 'guest' : name);
```

这是处理可空值时最常见、也最安全的写法之一。

### `!`

作用：强制非空。意思是“我确定这里一定不是 `null`”。

```dart
print(name!.length);
```

例子：

```dart
String? name = 'Tom';
print(name!.length); // 3
```

但如果判断错了：

```dart
String? name = null;
// print(name!.length); // 运行时会报错
```

所以 `!` 的意思不是“把 null 变没”，而是：

- 你向编译器保证这里一定有值
- 如果你保证错了，运行时就会炸

## 怎么选择这四个操作符

- 想声明“允许为空” -> `?`
- 想安全地往后访问属性或方法 -> `?.`
- 想给空值一个默认结果 -> `??`
- 想强行告诉编译器“这里不可能为空” -> `!`

## 一个连起来的例子

```dart
String? name;

print(name?.length); // 安全访问
print(name ?? 'guest'); // 默认值
```

如果你直接写：

```dart
// print(name.length); // 不可以，因为 name 可能是 null
```

编译器会拦住你，因为 `name` 是 `String?`，不是普通 `String`。

## 最实用建议

- 优先用 `?.` 和 `??`
- 少用 `!`
- 如果编译器提示你可能为空，优先思考数据流而不是强压过去
