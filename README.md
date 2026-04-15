# 📦 xb_logs_util

A lightweight Flutter log utility for local file storage, querying, zipping, and sharing logs.

一个轻量级 Flutter 日志工具库，支持 **日志落盘、本地查询、压缩打包、分享导出**，方便线上问题排查。

---

## ✨ Features

- 📝 Write structured logs (Map / JSON)
- 📁 Save logs to local file system
- 📅 Query logs by day / month
- 🗑️ Delete logs by date
- 📦 Zip selected logs
- 📤 Share log files (for debugging)
- ⚡ Simple API, easy integration

---

## 📁 Directory Structure

日志默认存储结构：

```
ApplicationDocumentsDirectory/
└── xbLogs/
    └── yyyy-MM-dd/
        ├── yyyy-MM-dd HH:mm:ss-SSS.txt
        ├── yyyy-MM-dd HH:mm:ss-SSS.txt
```

---

## 🚀 Getting Started

### 1. Add dependency

```yaml
dependencies:
  xb_logs_util: latest_version
```

---

### 2. Import

```dart
import 'package:xb_logs_util/xb_logs_util.dart';
```

---

## 🧩 Usage

### 1️⃣ 写日志（推荐）

```dart
await XBLogsUtil.writeLog({
  "event": "login",
  "userId": "123",
  "status": "success",
});
```

---

### 2️⃣ 写字符串日志

```dart
await XBLogsUtil.writeText("This is a log message");
```

---

### 3️⃣ 获取某天日志列表

```dart
final logs = await XBLogsUtil.getLogsByDay(DateTime.now());
```

---

### 4️⃣ 获取某月日志

```dart
final logs = await XBLogsUtil.getLogsByMonth(DateTime.now());
```

---

### 5️⃣ 删除某天日志

```dart
await XBLogsUtil.deleteLogsByDay(DateTime.now());
```

---

### 6️⃣ 压缩日志为 ZIP

```dart
final zipPath = await XBLogsUtil.zipLogs(logFiles);
```

---

### 7️⃣ 分享日志文件

```dart
await XBLogsUtil.shareLogs(zipPath);
```

---

## 📦 Example

你可以在 `example/` 目录查看完整示例：

```bash
cd example
flutter run
```

---

## 🧠 Use Cases

- App 崩溃日志收集
- 用户问题反馈
- 线上 bug 排查
- 网络请求日志记录
- 行为埋点调试

---

## ⚠️ Notes

- 日志默认存储在 **App 沙盒目录**
- iOS 无法直接访问文件系统，需要通过“分享”导出
- Android 可配合文件管理器查看
- 建议定期清理日志，避免占用过多空间

---

## 🔐 Permissions

如需分享文件，请确保已配置：

### Android

```xml
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
```

（Android 10+ 建议使用 scoped storage）

---

## 📄 License

MIT License © 2026 xie xianbin

---

## 🙌 Contribution

PR & Issue welcome!

---

## ⭐ Support

如果这个项目对你有帮助，欢迎点个 ⭐️
