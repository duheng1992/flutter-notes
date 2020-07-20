# flutter-notes

Dart语法： https://www.dartcn.com/samples/

## 1、flutter安装
* https://flutter.dev/docs/get-started/install/macos 官网下载安装包，解压缩到本地目录
* 配置环境变量

    ```
      vim ~/.bash_profile
    
        export PUB_HOSTED_URL=https://pub.flutter-io.cn
        export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
        export PATH=/Users/abc/APP/flutter/bin:$PATH  这里写上自己的安装目录（到bin）

      source ~/.bash_profile
   ```
   
 * 检查是否配置正确 flutter -h （翻墙状态，等待片刻）
 * 检查flutter环境 flutter doctor
 
