# DJ 音标训练

DJ 音标（英式、非卷舌）基础学习应用：48 个音标，点卡片即可听发音，含知识讲解和听音选音标、顺序跟读练习，学习进度保存在本地。

当前阶段只做基础音标学习，背单词功能以后再加。

## 网页版

直接用浏览器打开根目录的 `index.html` 即可离线使用，无需登录、无广告、无联网。

`index.html` 与安卓版 `app/src/main/assets/index.html` 是同一份内容。

## 安卓版

安卓版是一个 WebView 壳：`MainActivity` 加载 `app/src/main/assets/index.html`，开启 JavaScript 和 DOM 存储（学习进度用 localStorage 保存），不申请联网权限。

- 包名：`com.dj.phonetics`
- 应用名：DJ音标训练
- 版本：1.0（versionCode 1）
- minSdk 24，targetSdk / compileSdk 34，AGP 8.5.2，Gradle 8.7，JDK 17

构建（需要 Android SDK，含 build-tools 35.0.0 和 platforms android-34）：

```bash
./gradlew assembleDebug
```

产物在 `app/build/outputs/apk/debug/app-debug.apk`。

注意：仓库里没有 `gradle/wrapper/gradle-wrapper.jar`（二进制文件），也没有编译产物和已签名的 APK。`gradlew` 第一次运行时会按 `gradle/wrapper/gradle-wrapper.properties` 下载 Gradle 8.7；也可以直接用本地已装的 Gradle 8.7 构建。已交付的 APK 是 debug 版（未做 release 签名），安装时需允许“安装未知应用”。

## 目录

- `index.html`：网页版（48 音标 + 音频 + 讲解 + 练习）
- `app/src/main/assets/index.html`：安卓版内嵌的同一份网页
- `app/src/main/java/com/dj/phonetics/MainActivity.java`：WebView 壳
- `app/src/main/AndroidManifest.xml`、`app/src/main/res/`：应用清单与资源
- `build.gradle`、`settings.gradle`、`app/build.gradle`、`gradle.properties`：Gradle 配置
