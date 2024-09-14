# Android环境配置和构建

在开始之前，请确保您已经正确设置了以下环境变量和依赖项：

## 环境变量

1. **ANDROID_SDK**: 指向您的Android SDK安装目录的路径。例如：`/Users/yourusername/Library/Android/sdk`
2. **ANDROID_HOME**: 和ANDROID_SDK一样，指向您的Android SDK安装目录的路径。
3. **NDK_PATH**: 指向您的Android NDK 16安装目录的路径。例如：`/Users/yourusername/Library/Android/sdk/ndk/16.1.4479499`

**注意**：您可以选择将这些环境变量直接设置在`mac_build.sh`脚本文件中。此外，请确保已安装**NDK 16**。您可以从[这里](https://developer.android.com/ndk/downloads/older_releases)下载旧版本的NDK。

## 构建步骤

完成上述环境变量设置后，请按照以下步骤进行构建：

1. 打开终端，导航到`util/buildscripts`目录。
2. 在该目录下，运行以下命令执行构建脚本：

```bash
chmod +x mac_build.sh
./mac_build.sh
```

## 踩坑
如果遇到这个报错：
```
-- Could NOT find LLVM (missing: LLVM_DIR)
CMake Error at renderdoc/CMakeLists.txt:531 (message):
  LLVM not found - interceptor-lib requires LLVM 4.0 available.
```

可以删除renderdoc根目录下的build和build-android-arm32目录

也可以重新手动构建一下Android：

```bash
cd ~/CLionProjects/renderdoc
rm -rf build-android-arm32
mkdir build-android-arm32
cd build-android-arm32
cmake -DLLVM_DIR=/opt/homebrew/opt/llvm/lib/cmake/llvm ..
cd ..
```