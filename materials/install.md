
<a href="https://github.com/drshahizan/mobile_apps/stargazers"><img src="https://img.shields.io/github/stars/drshahizan/mobile_apps" alt="Stars Badge"/></a>
<a href="https://github.com/drshahizan/mobile_apps/network/members"><img src="https://img.shields.io/github/forks/drshahizan/mobile_apps" alt="Forks Badge"/></a>
<a href="https://github.com/drshahizan/mobile_apps/pulls"><img src="https://img.shields.io/github/issues-pr/drshahizan/mobile_apps" alt="Pull Requests Badge"/></a>
<a href="https://github.com/drshahizan/mobile_apps/issues"><img src="https://img.shields.io/github/issues/drshahizan/mobile_apps" alt="Issues Badge"/></a>
<a href="https://github.com/drshahizan/mobile_apps/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/drshahizan/mobile_apps?color=2b9348"></a>
![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan%2Fmobile_apps&labelColor=%23d9e3f0&countColor=%23697689&style=flat)


# Software Required for Building Mobile Apps with Flutter

To develop mobile apps (for Android and iOS) using Flutter, you'll need to install specific software tools and SDKs. Flutter is cross-platform, so you can build for both platforms from one codebase, but iOS development requires a macOS machine. Below is a comprehensive list of what you need to install and know about. This assumes you're starting from scratch; follow the official Flutter documentation for detailed setup (https://docs.flutter.dev/get-started/install).

## 1. **Flutter SDK**
   - **Why?**: This is the core framework for building Flutter apps. It includes the Dart programming language, widgets, and tools for compilation.
   - **Installation**:
     - Download from the official site: https://flutter.dev.
     - Extract to a directory (e.g., `C:\src\flutter` on Windows or `~/development/flutter` on macOS/Linux).
     - Add the `bin` folder to your system's PATH environment variable.
   - **What to Know**: Run `flutter doctor` in your terminal/command prompt after installation to check for issues and verify setup. This command also helps install missing dependencies.
   - **Version**: Use the stable channel for beginners (`flutter channel stable` then `flutter upgrade`).

## 2. **Dart SDK**
   - **Why?**: Flutter uses Dart as its programming language. It's bundled with the Flutter SDK, so no separate installation is needed.
   - **What to Know**: Learn basic Dart syntax (variables, functions, classes) as it's essential for writing Flutter code. Resources: Dart official tour (https://dart.dev/guides/language/language-tour).

## 3. **Android Studio (for Android Development)**
   - **Why?**: Provides the Android SDK, emulators, and tools for building and testing Android apps. It's also a great IDE for Flutter.
   - **Installation**:
     - Download from: https://developer.android.com/studio.
     - During setup, install the Android SDK, Android SDK Command-line Tools, and Android Emulator.
     - Install Flutter and Dart plugins in Android Studio (via Settings > Plugins).
   - **What to Know**:
     - Accept Android licenses via `flutter doctor --android-licenses`.
     - Set up an Android Virtual Device (AVD) for emulation.
     - Minimum SDK version: Android 4.1 (API 16), but target newer for better performance.
   - **Alternatives**: You can use command-line tools only, but Android Studio is recommended for its integrated features.

## 4. **Xcode (for iOS Development, macOS Only)**
   - **Why?**: Required for building, simulating, and deploying iOS apps. Flutter compiles to native iOS code using Xcode tools.
   - **Installation**:
     - Download from the Mac App Store (free).
     - Install Command Line Tools: Run `xcode-select --install` in Terminal.
     - Accept the license: `sudo xcodebuild -license accept`.
   - **What to Know**:
     - You need a Mac for iOS development (no Windows/Linux workaround for building iOS apps).
     - Set up an iOS Simulator in Xcode.
     - For physical device testing, enroll in Apple's Developer Program (free for testing, paid for distribution).
     - CocoaPods (dependency manager) may be needed; install via `sudo gem install cocoapods` if `flutter doctor` flags it.

## 5. **Integrated Development Environment (IDE)**
   - **Why?**: For writing, debugging, and running code efficiently.
   - **Recommended Options**:
     - **Visual Studio Code (VS Code)**: Lightweight and popular for Flutter.
       - Download: https://code.visualstudio.com.
       - Install extensions: "Flutter" and "Dart" from the Extensions marketplace.
       - What to Know: Supports hot reload, debugging, and IntelliSense for code completion.
     - **Android Studio**: If already installed for Android, use it as your IDE (has built-in Flutter support).
     - **IntelliJ IDEA**: Similar to Android Studio, community edition is free.
   - **What to Know**: VS Code is great for beginners due to its simplicity; Android Studio offers more Android-specific tools.

## 6. **Git (Version Control)**
   - **Why?**: Essential for managing code versions, collaborating, and installing dependencies via pub (Dart's package manager).
   - **Installation**: Download from https://git-scm.com/downloads.
   - **What to Know**: Basic commands like `git clone`, `git commit`, `git push`. Flutter projects often use Git for source control.

## Additional Tools and Considerations
- **Chrome Browser**: Useful if you want to test web versions of your app (`flutter run -d chrome`), but not strictly needed for mobile.
- **System Requirements**:
  - **Operating System**: Windows (10+), macOS (11+ for Xcode), Linux (Ubuntu 20.04+ or similar).
  - **Hardware**: 64-bit processor, at least 8GB RAM (16GB recommended), 10GB+ free disk space.
  - **Internet**: For downloading SDKs and dependencies.
- **Package Manager**: Flutter uses `pub` (built-in) for adding libraries (e.g., `flutter pub add provider`).
- **Testing Devices**: 
  - Android: Emulator or physical device with USB debugging enabled.
  - iOS: Simulator or physical iPhone/iPad.
- **Optional but Useful**:
  - Firebase CLI: For backend integration (authentication, database).
  - Visual Studio (Windows only): For desktop app extensions, but not for mobile.

## Getting Started Steps
1. Install Flutter SDK and add to PATH.
2. Run `flutter doctor` to identify and fix issues.
3. Install Android Studio and/or Xcode based on your target platforms.
4. Set up your IDE.
5. Create a new project: `flutter create my_app`.
6. Run it: `flutter run` (with a device connected).

If you're on Windows/Linux and want iOS apps, you'll need a Mac or use cloud services like Codemagic for builds. Focus on learning Dart and Flutter widgets next—start with the official codelabs! If you encounter issues, check `flutter doctor` output or forums like Stack Overflow.

## Contribution 🛠️
Please create an [Issue](https://github.com/drshahizan/mobile_apps/issues) for any improvements, suggestions or errors in the content.

You can also contact me using [Linkedin](https://www.linkedin.com/in/drshahizan/) for any other queries or feedback.

[![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fdrshahizan&labelColor=%23697689&countColor=%23555555&style=plastic)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fdrshahizan)
![](https://hit.yhype.me/github/profile?user_id=81284918)

