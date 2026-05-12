# 05 补充：字符串插值

对应主文档章节：`5. 字符串插值`

## 为什么推荐字符串插值

相比字符串拼接：

```dart
print('name: ' + name);
```

更推荐：

```dart
print('name: $name');
```

优点：

- 更短
- 更易读
- 表达式场景更自然

## 两种常见写法

```dart
print('$name');
print('${age + 1}');
```

规则：

- 单个变量用 `$变量名`
- 复杂表达式用 `${表达式}`

## 多行字符串

```dart
var text = '''
line 1
line 2
''';
```

## Flutter 里常见场景

- 调试输出：`debugPrint('route: ${settings.name}');`
- 文案拼接：`Text('Hello, $name')`
