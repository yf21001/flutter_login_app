# 快速开始指南

## 📱 应用概述

这是一个简单的 Flutter 登录应用，包含：
- 登录页面（手机号 + 验证码）
- 欢迎页面（显示登录成功）

## 🚀 快速构建 APK

### 方案 1：在线构建（推荐 - 无需本地环境）

#### 使用 Codemagic（最简单）

1. **上传项目到 GitHub**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/flutter_login_app.git
   git push -u origin main
   ```

2. **在 Codemagic 上构建**
   - 访问 https://codemagic.io
   - 用 GitHub 账号登录
   - 点击 "Add application"
   - 选择您的仓库
   - 点击 "Build" 开始构建
   - 构建完成后下载 APK

### 方案 2：本地构建（需要环境配置）

#### 前置条件

```bash
# 1. 安装 Flutter（如果未安装）
# 访问 https://flutter.dev/docs/get-started/install

# 2. 验证安装
flutter doctor

# 3. 获取依赖
flutter pub get

# 4. 构建 APK
flutter build apk --release
```

#### 构建完成

APK 文件位置：
```
build/app/outputs/flutter-apk/app-release.apk
```

## 🧪 测试应用

### 测试账号

| 项目 | 值 |
|------|-----|
| 手机号 | 13888888888 |
| 验证码 | 123456 |

### 测试流程

1. 打开应用
2. 输入手机号：`13888888888`
3. 输入验证码：`123456`
4. 点击"登录"
5. 进入欢迎页面

## 📁 项目文件说明

| 文件 | 说明 |
|------|------|
| `lib/main.dart` | 应用主文件（包含所有代码） |
| `pubspec.yaml` | 项目配置和依赖 |
| `android/app/build.gradle` | Android 构建配置 |
| `android/app/src/main/AndroidManifest.xml` | Android 应用清单 |
| `BUILD_INSTRUCTIONS.md` | 详细构建说明 |
| `README_CN.md` | 中文项目说明 |

## 🔧 常见自定义

### 修改测试账号

编辑 `lib/main.dart`，找到 `_login()` 方法：

```dart
if (phone == '13888888888' && code == '123456') {
  // 修改这里
}
```

### 修改应用名称

编辑 `android/app/src/main/AndroidManifest.xml`：

```xml
android:label="您的应用名称"
```

### 修改应用包名

编辑 `android/app/build.gradle`：

```gradle
applicationId = "com.yourcompany.yourapp"
```

## 📚 更多资源

- **Flutter 官方文档**：https://flutter.dev/docs
- **Dart 语言文档**：https://dart.dev
- **Material Design**：https://material.io/design
- **Codemagic 文档**：https://docs.codemagic.io

## ❓ 常见问题

**Q: 如何修改应用图标？**
A: 替换 `android/app/src/main/res/mipmap-*/ic_launcher.png`

**Q: 如何修改启动屏幕？**
A: 编辑 `android/app/src/main/res/drawable/launch_background.xml`

**Q: 如何连接真实后端？**
A: 在 `_login()` 方法中使用 `http` 或 `dio` 包发送 API 请求

**Q: 如何发布到应用商店？**
A: 参考 Flutter 官方文档的 [发布指南](https://flutter.dev/docs/deployment)

## 💡 下一步

- 添加真实的后端 API 集成
- 实现密码登录功能
- 添加用户注册页面
- 实现本地数据存储
- 添加推送通知功能

---

**需要帮助？** 查看 `BUILD_INSTRUCTIONS.md` 获取更详细的说明。
