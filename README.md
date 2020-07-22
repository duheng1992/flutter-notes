# flutter-notes

> 多端开发：

> cordova / ionic  js编译，图形性能差  30帧

> rn 多个view进行合并编译，强于h5，60帧

> 小程序 平台限制 体量限制

> flutter 谷歌移动UI框架，免费开源，前景好 性能最好, 整体GPU渲染 120fps
 
* 开源项目
https://flutterchina.club/opensource.html

* 企业应用
   闲鱼， google ads ...  https://flutter.io/showcase/

* 生态
https://github.com/Solido/awesome-flutter

Dart语法： https://www.dartcn.com/samples/

## 1、flutter安装
* https://flutter.dev/docs/get-started/install/macos 官网下载安装包，解压缩到本地目录（翻墙）
* 配置环境变量

    ```shell
      vim ~/.bash_profile
    
        export PUB_HOSTED_URL=https://pub.flutter-io.cn
        export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
        export PATH=/Users/abc/APP/flutter/bin:$PATH  这里写上自己的安装目录（到bin）

      source ~/.bash_profile
   ```
   
 * 检查是否配置正确 flutter -h （翻墙状态，等待片刻）
 * 检查flutter环境 flutter doctor
![](https://github.com/duheng1992/flutter-notes/blob/master/flutter-doctor.png?raw=true)
    按照报告安装缺失的文件

  * 安装 Android Studio 
    官网： https://developer.android.com/studio/index.html
    配置路径
    ```js
     export ANDROID_HOME="/Users/abc/Library/Android/sdk"
	 export PATH=${PATH}:${ANDROID_HOME}/tools
	 export PATH=${PATH}:${ANDROID_HOME}/platform-tools
    ```
    
    安装flutter插件
    ![](https://github.com/duheng1992/flutter-notes/blob/master/android-studio2.png)
    
    安装好后执行
    ```shell
    flutter doctor --android-licenses
```
  * 安装xcode
  appstore下载
  > 常见问题：CocoaPods not installed ==> 处理方式： brew install cocoapods
  
  * homebrew安装
  ```shell
    /bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
  ```
  
  ## 2、开始一个项目
  ```shell
  sudo flutter create demo-1
  ```
  给项目和sdk赋予权限
  ```shell
    sudo chmod -R 777 * 
  ```
  > （坑：重新打开终端发现flutter指令失效：source ~/.bath_profile只在当前会话生效，新版mac（catalina以后）把zsh作为shell脚本，默认不会加载.bash_profile, 需在.zshrc文件中加入相关配置）
  
  
  ## 3、常用组件
