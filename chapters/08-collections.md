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

## 各种集合怎么读和写

## `List` 的读写

`List` 最像“有顺序的数组”。

### 读取

```dart
var numbers = [10, 20, 30];

print(numbers[0]); // 10
print(numbers[1]); // 20
print(numbers.length); // 3
```

- 通过下标读取：`list[index]`
- 下标从 `0` 开始

### 写入

```dart
var numbers = [10, 20, 30];

numbers[0] = 99;
numbers.add(40);
numbers.remove(20);
```

- 改某一项：`list[index] = value`
- 末尾追加：`list.add(value)`
- 删除某个值：`list.remove(value)`

## `Map` 的读写

`Map` 最像“键值对字典”。

### 读取

```dart
var user = {
  'name': 'Tom',
  'age': 18,
};

print(user['name']); // Tom
print(user['age']); // 18
print(user.keys); // (name, age)
```

- 通过 key 读取：`map['key']`
- 读取不到时，结果通常是 `null`

### 写入

```dart
var user = {
  'name': 'Tom',
};

user['age'] = 18; // 新增
user['name'] = 'Jack'; // 修改
user.remove('name'); // 删除
```

- 新增和修改都用：`map['key'] = value`
- 删除用：`map.remove('key')`

## `Set` 的读写

`Set` 最像“自动去重的集合”。

### 读取

```dart
var ids = <int>{1, 2, 3};

print(ids.contains(2)); // true
print(ids.length); // 3
```

- 常见读取不是按下标，而是判断是否包含某个值
- `Set` 一般不强调顺序

### 写入

```dart
var ids = <int>{1, 2, 3};

ids.add(4);
ids.add(2); // 不会重复添加
ids.remove(1);
```

- 添加：`set.add(value)`
- 删除：`set.remove(value)`
- 重复值不会存两份

## 一个快速对比

- `List`：按下标读写，适合有顺序的数据
- `Map`：按 key 读写，适合键值对数据
- `Set`：按“是否包含某个值”来判断，适合去重

## Flutter 场景

- `List<Widget>`：页面上的一组组件
- `Map<String, dynamic>`：接口返回 JSON
- `Set<String>`：去重标签、选中项集合
