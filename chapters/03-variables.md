# 03 补充：变量 `var`、`final`、`const`

对应主文档章节：`3. 变量：var、final、const`

## 一张对照表

| 写法 | 是否可重新赋值 | 值何时确定 | 常见用途 |
| --- | --- | --- | --- |
| `var` | 可以 | 运行时 | 临时变量 |
| `final` | 不可以 | 运行时 | 大多数局部变量 |
| `const` | 不可以 | 编译时 | 常量、常量 Widget |

## 三个最常见误区

### 1. `var` 不是动态类型

```dart
var count = 1;
// count = '1'; // 不可以
```

### 2. `final` 不是“绝对不可变”

```dart
final list = [1, 2];
list.add(3); // 可以，变的是对象内容
```

### 3. `const` 比 `final` 更严格

```dart
final now = DateTime.now(); // 可以
// const now = DateTime.now(); // 不可以
```

## Flutter 中的经验

- 默认优先考虑 `final`
- 值明显固定时用 `const`
- 只有确实会变化时才用 `var`
