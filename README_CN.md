# 简单登录应用 - Flutter

一个简洁的 Flutter 登录应用示例，展示了基本的登录流程和页面导航。

## 功能特性

✅ **登录页面**
- 手机号输入框（支持中国手机号格式验证）
- 验证码输入框
- 登录按钮（带加载动画）
- 测试账号提示

✅ **登录逻辑**
- 模拟验证码验证
- 表单验证和错误提示
- 登录成功后的页面跳转

✅ **欢迎页面**
- 显示登录成功状态
- 显示用户手机号
- 退出登录功能

## 快速开始

### 前置条件

- Flutter SDK（版本 3.5.0 或更高）
- Dart SDK（通常随 Flutter 一起安装）
- Android SDK（用于构建 APK）

### 安装依赖

```bash
flutter pub get
```

### 运行应用

```bash
flutter run
```

### 构建 APK

```bash
flutter build apk --release
```

## 测试账号

| 项目 | 值 |
|------|-----|
| 手机号 | 13888888888 |
| 验证码 | 123456 |

## 项目结构

```
lib/
├── main.dart
│   ├── MyApp              # 应用主类
│   ├── LoginPage          # 登录页面
│   └── WelcomePage        # 欢迎页面
```

## 代码说明

### LoginPage（登录页面）

- 使用 `StatefulWidget` 管理表单状态
- `_phoneController` 和 `_codeController` 分别管理手机号和验证码输入
- `_login()` 方法处理登录逻辑和验证
- 使用 `Navigator.pushReplacement()` 跳转到欢迎页面

### WelcomePage（欢迎页面）

- 使用 `StatelessWidget` 展示静态内容
- 接收 `phoneNumber` 参数并显示
- 提供"退出登录"按钮返回登录页面

## 自定义配置

### 修改测试账号

编辑 `lib/main.dart` 中的验证逻辑：

```dart
if (phone == '13888888888' && code == '123456') {
  // 修改这里的手机号和验证码
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

## 连接真实后端

如果需要连接真实的后端 API，可以使用 `http` 或 `dio` 包：

```bash
flutter pub add http
```

然后修改 `_login()` 方法：

```dart
void _login() async {
  final response = await http.post(
    Uri.parse('https://your-api.com/login'),
    body: {
      'phone': _phoneController.text,
      'code': _codeController.text,
    },
  );
  
  if (response.statusCode == 200) {
    // 登录成功
  } else {
    // 登录失败
  }
}
```

## 在线构建

如果您不想在本地配置 Flutter 环境，可以使用以下在线服务：

- **Codemagic**：https://codemagic.io
- **AppCenter**：https://appcenter.ms
- **GitHub Actions**：配置自动化构建流程

详见 `BUILD_INSTRUCTIONS.md`。

## 应用截图

### 登录页面
- 标题："欢迎登录"
- 手机号输入框
- 验证码输入框
- 登录按钮
- 测试账号提示

### 欢迎页面
- 成功图标（绿色勾号）
- 标题："登录成功"
- 欢迎文本："欢迎 [手机号] 登录"
- 退出登录按钮

## 技术栈

- **框架**：Flutter 3.24.0
- **语言**：Dart 3.5.0
- **UI 框架**：Material Design 3
- **状态管理**：setState（简单应用）

## 常见问题

**Q: 如何修改应用图标？**

A: 将新的图标文件放在以下目录：
- `android/app/src/main/res/mipmap-*/ic_launcher.png`

**Q: 如何修改应用启动屏幕？**

A: 编辑 `android/app/src/main/res/drawable/launch_background.xml`

**Q: 如何增加新的页面？**

A: 创建新的 `StatefulWidget` 或 `StatelessWidget`，然后在 `Navigator` 中使用 `pushReplacement()` 或 `push()` 进行页面跳转。

## 许可证

MIT License - 可自由使用和修改

## 贡献

欢迎提出 Issue 和 Pull Request！

---

**最后更新**：2025 年 11 月 25 日
