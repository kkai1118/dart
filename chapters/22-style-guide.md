# 22 补充：推荐书写习惯

对应主文档章节：`22. 推荐书写习惯`

## 一个简单优先级

- 先想能不能用 `const`
- 不行就优先 `final`
- 确实会变化再用 `var`

例如：

```dart
const appName = 'Demo';
final now = DateTime.now();
var count = 0;
```

这个优先级的核心是：默认尽量减少可变状态。

## 类型写法建议

- 类型很明显时可用 `var`
- 类型不明显或很关键时直接写出类型
- 公共 API、模型对象字段尽量写明确类型

### 适合用 `var` 的情况

```dart
var name = 'Tom';
var list = <String>[];
```

这种场景下，类型一眼就能看出来。

### 更适合写明确类型的情况

```dart
Future<String> fetchName() async {
  return 'Tom';
}

final Map<String, dynamic> user = {};
```

这种写法更适合：

- 返回值比较关键
- 类型不那么直观
- 需要让读代码的人一眼看懂

## 布尔变量命名建议

布尔值最好让人一看就知道“这是一个 true / false 问题”。

例如：

- `isLogin`
- `isReady`
- `hasData`
- `canEdit`

不太推荐：

- `loginFlag`
- `dataStatus`

前者读起来更自然。

## 函数命名建议

函数名尽量体现动作。

例如：

- `loadData`
- `fetchUser`
- `saveOrder`
- `goToHome`

这样别人看到名字时，马上知道“这个函数是做什么的”。

## 类和文件命名建议

- 类名：大驼峰，如 `HomePage`
- 变量名 / 函数名：小驼峰，如 `homePage`、`loadData`
- 文件名：通常用下划线风格，如 `home_page.dart`

这样会更符合 Dart / Flutter 的常见项目习惯。

## 调试建议

- Flutter 中优先用 `debugPrint`
- 调试输出带上上下文，比如模块名、字段名

例如：

```dart
debugPrint('login page submit clicked, phone: $phone');
```

比下面这种更有价值：

```dart
debugPrint('clicked');
```

## 命名建议

- 类名用大驼峰：`HomePage`
- 变量和函数用小驼峰：`homePage`, `loadData`
- 常量名也常用小驼峰：`homeRoute`

## 一个额外建议：少写“又短又模糊”的名字

不太推荐：

```dart
var a = 'Tom';
var b = 18;
```

更推荐：

```dart
var userName = 'Tom';
var userAge = 18;
```

变量名稍微清楚一点，后面读代码会轻松很多。

## 写代码时的一个小原则

不是为了“写得最短”，而是为了“过几天回来看还能快速看懂”。
