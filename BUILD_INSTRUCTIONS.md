# Flutter 登录应用构建说明

## 项目概述

这是一个简单的 Flutter 登录应用，包含以下功能：

- **登录页面**：用户输入手机号和验证码进行登录
- **验证码验证**：模拟验证码验证（测试账号：13888888888，验证码：123456）
- **欢迎页面**：登录成功后显示欢迎信息和用户手机号

## 项目结构

```
flutter_login_app/
├── lib/
│   └── main.dart          # 应用主文件（包含登录页和欢迎页）
├── android/               # Android 配置文件
├── pubspec.yaml          # Flutter 依赖配置
└── README.md             # 项目说明
```

## 本地构建方法

### 前置条件

1. **安装 Flutter SDK**
   - 访问 [Flutter 官网](https://flutter.dev/docs/get-started/install) 下载并安装 Flutter
   - 配置 PATH 环境变量

2. **安装 Android SDK**
   - 通过 Android Studio 或命令行工具安装
   - 配置 `ANDROID_HOME` 环境变量

3. **安装 Java JDK**
   - 需要 Java 11 或更高版本

### 构建 APK

在项目根目录执行以下命令：

```bash
# 获取依赖
flutter pub get

# 构建 Release APK
flutter build apk --release
```

构建完成后，APK 文件位置：
```
build/app/outputs/flutter-apk/app-release.apk
```

## 在线构建方法（推荐）

如果您不想在本地配置 Flutter 和 Android SDK，可以使用以下在线服务：

### 方案 1：使用 Codemagic（推荐）

1. 访问 [Codemagic](https://codemagic.io)
2. 使用 GitHub 账号登录
3. 将此项目上传到 GitHub
4. 在 Codemagic 中连接您的 GitHub 仓库
5. 配置构建设置（使用默认配置即可）
6. 点击"Build"开始构建
7. 构建完成后下载 APK 文件

### 方案 2：使用 AppCenter

1. 访问 [Microsoft AppCenter](https://appcenter.ms)
2. 使用 Microsoft 账号登录
3. 创建新应用
4. 连接 GitHub 仓库
5. 配置构建设置
6. 开始构建并下载 APK

### 方案 3：使用 GitHub Actions

在项目根目录创建 `.github/workflows/build.yml` 文件，配置自动化构建流程。

## 测试账号

- **手机号**：13888888888
- **验证码**：123456

## 应用功能说明

### 登录页面

- 输入手机号（必须是有效的中国手机号格式）
- 输入验证码
- 点击"登录"按钮
- 验证成功后跳转到欢迎页面

### 欢迎页面

- 显示"登录成功"提示
- 显示"欢迎 [手机号] 登录"
- 点击"退出登录"按钮返回登录页面

## 自定义配置

### 修改测试账号

编辑 `lib/main.dart` 文件，找到 `_login()` 方法中的验证逻辑：

```dart
if (phone == '13888888888' && code == '123456') {
  // 登录成功
}
```

修改手机号和验证码即可。

### 修改应用名称

编辑 `android/app/src/main/AndroidManifest.xml`：

```xml
android:label="简单登录"
```

### 修改应用包名

编辑 `android/app/build.gradle`：

```gradle
applicationId = "com.example.flutter_login_app"
```

## 常见问题

### Q: 如何修改应用图标？

A: 将新的图标文件放在以下目录：
- Android: `android/app/src/main/res/mipmap-*/ic_launcher.png`
- iOS: `ios/Runner/Assets.xcassets/AppIcon.appiconset/`

### Q: 如何修改应用启动屏幕？

A: 编辑以下文件：
- Android: `android/app/src/main/res/drawable/launch_background.xml`
- iOS: `ios/Runner/Assets.xcassets/LaunchImage.imageset/`

### Q: 如何连接真实的后端 API？

A: 修改 `lib/main.dart` 中的 `_login()` 方法，使用 `http` 或 `dio` 包发送 HTTP 请求到您的后端服务器。

## 许可证

此项目为示例项目，可自由使用和修改。

## 联系方式

如有问题，请提出 Issue 或 Pull Request。
