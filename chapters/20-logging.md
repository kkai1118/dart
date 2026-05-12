# 20 补充：`print`、`debugPrint`、`log`

对应主文档章节：`20. print、debugPrint、log 的区别`

## 一句话区分

- `print`：最基础输出
- `debugPrint`：Flutter 调试输出
- `log`：更结构化的日志 API

## 参数类型差异

```dart
print(123); // 可以
```

```dart
// debugPrint(123); // 不可以
```

因为 `debugPrint` 接收的是 `String?`，而不是任意对象。

## 当前项目里该怎么选

- 临时调试页面和路由：`debugPrint`
- 正式日志体系：再考虑 `log` 或日志框架
- 不建议在生产代码里长期保留大量 `print`
