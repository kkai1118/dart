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

## 补充：集合推导里的 `for`

Flutter 中很常见：

```dart
var labels = [for (final n in [1, 2, 3]) 'item $n'];
```

这在写 Widget 列表时非常实用。
