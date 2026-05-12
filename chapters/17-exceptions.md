# 17 补充：异常处理

对应主文档章节：`17. 异常处理`

## 基本结构

```dart
try {
  doSomething();
} catch (e, stackTrace) {
  print('error: $e');
}
```

## 三个部分分别做什么

- `try`：放可能出错的代码
- `catch`：捕获错误对象
- `stackTrace`：错误调用栈，便于定位问题

## 可选的 `finally`

```dart
try {
  open();
} finally {
  close();
}
```

即使出错，`finally` 里的清理逻辑也会执行。

## 实战建议

- 不要吞掉异常后什么都不做
- 至少记录日志，保留定位信息
- 对用户可见的失败场景，给出明确提示
