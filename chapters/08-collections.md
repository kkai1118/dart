# 08 补充：集合 `List`、`Map`、`Set`

对应主文档章节：`8. 集合：List、Map、Set`

## 先判断你需要哪种集合

- 有顺序、可按下标取值：`List`
- 键值对：`Map`
- 去重集合：`Set`

## 空集合的写法

```dart
var list = <int>[];
var map = <String, int>{};
var set = <int>{};
```

注意：`{}` 默认更容易被当成 `Map`，声明 `Set` 时最好显式写类型。

## 常见操作

```dart
var numbers = [1, 2, 3];
numbers.add(4);
numbers.remove(2);
```

```dart
var user = {'name': 'Tom'};
user['age'] = 18;
```

```dart
var ids = <int>{1, 2, 3};
ids.add(2); // 不会重复添加
```

## Flutter 场景

- `List<Widget>`：页面上的一组组件
- `Map<String, dynamic>`：接口返回 JSON
- `Set<String>`：去重标签、选中项集合
