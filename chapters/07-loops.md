# 07 补充：循环

对应主文档章节：`7. 循环`

## 三种高频循环

### `for`

适合知道循环次数时使用。

```dart
for (var i = 0; i < 3; i++) {
  print(i);
}
```

### `for-in`

适合遍历集合。

```dart
for (final item in ['a', 'b', 'c']) {
  print(item);
}
```

### `while`

适合“条件满足就继续”。

```dart
while (count < 3) {
  count++;
}
```

## `break` 和 `continue`

### `break`

表示：直接结束整个循环。

```dart
for (var i = 0; i < 10; i++) {
  if (i == 3) {
    break;
  }
  print(i);
}
```

这段代码会在 `i == 3` 时停止循环。

### `continue`

表示：跳过当前这一轮，继续下一轮。

```dart
for (var i = 0; i < 5; i++) {
  if (i == 2) {
    continue;
  }
  print(i);
}
```

这里会跳过 `2`，继续后面的循环。

## `forEach` 是什么

有时你会看到这种写法：

```dart
final list = ['a', 'b', 'c'];

list.forEach((item) {
  print(item);
});
```

它本质上也是遍历集合。

## `for-in` 和 `forEach` 怎么选

### `for-in`

```dart
for (final item in list) {
  print(item);
}
```

优点：

- 更直观
- 更适合初学者
- 更方便配合 `break`、`continue`

### `forEach`

```dart
list.forEach((item) {
  print(item);
});
```

优点：

- 写法简洁
- 有时适合链式处理风格

初学阶段建议优先熟悉：

- `for`
- `for-in`
- `while`

再慢慢理解 `forEach`。

## 补充：集合推导里的 `for`

Flutter 中很常见：

```dart
var labels = [for (final n in [1, 2, 3]) 'item $n'];
```

这在写 Widget 列表时非常实用。

## Flutter 里常见循环场景

- 遍历接口返回的列表
- 生成一组 `Widget`
- 找到满足条件的数据后提前结束
- 跳过某些无效项
