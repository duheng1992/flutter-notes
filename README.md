# flutter-notes

多端开发：

> cordova / ionic  js编译，图形性能差  30帧

> rn 多个view进行合并编译，强于h5，60帧

> 小程序 平台限制 体量限制

> flutter 谷歌移动UI框架，免费开源，前景好 性能最好, 整体GPU渲染 120fps

|比较内容|	Flutter|	RN|	原生|
|----|----|----|----|
|APK大小|	5.5M|	6.6M|	1.4M|
|启动时间|	冷启动319ms，热启动152ms	|冷启动243ms，热启动71ms|	冷启动181ms， 热启动74.8ms|
|内存-cpu-魅蓝Metal|	初始30M ,滑动5000稳定后32M，cpu22%|	初始38M,滑动5000，稳定在60M,cpu45%|	初始：7.6M ,滑动5000条稳定在12M,cpu10%|
|内存-cpu-魅族Pro5|	初始85M ,滑动5000条稳定后110M，cpu12%|	初始56M,滑动5000，稳定在104M,cpu22%|	初始：29.5M ,滑动5000条稳定在42M,cpu7%|
|内存-cpu-华为P20Pro|	初始99M ,滑动5000条稳定110M，cpu12%|	初始63M,滑动5000，稳定在80M,cpu22%|	初始：25M ,滑动5000条稳定在32M,cpu8%|
|主观感受|	无卡顿	|滚动100条之后有卡顿	|丝滑|


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
  
  启动
  
  ```
    flutter run 
  ```
  
  依赖安装
  https://pub.flutter-io.cn/flutter/packages
  
  ## 3、常用组件

* Text()

|参数|说明|
|  ----  | ----  |
|textAlign|center / left / right / justify|
|textDirection|ltr / rtl|
|overflow|clip 裁剪，fade 渐隐，ellipsis 省略号|
|textScaleFactor|字体显示倍率|
|maxLines|-|
|style|TextStyle对象|

* TextStyle()

|参数|说明|
|  ----  | ----  |
|decoration|none 没有线，lineThrough 删除线，overline 上划线，underline 下划线|
|decorationColor|-|
|decorationStyle|[dashed,dotted]虚线，double 两根线，solid 一根实线，wavy 波浪线|
|wordSpacing|文字间隙|
|fontStyle|italic 斜体，normal 正常体 ...|
|letterSpacing|-|
|color|Color对象|
|fontSize|-|
|fontWeight|bold 粗体，normal 正常体|

* Container()

|参数|说明|
|  ----  | ----  |
|alignment|topCenter：顶部居中对齐<br> topLeft：顶部左对齐<br> topRight：顶部右对齐<br> center：水平垂直居中对齐<br> centerLeft：垂直居中水平居左对齐<br> centerRight：垂直居中水平居右对齐<br> bottomCenter 底部居中对齐<br> bottomLeft：底部居左对齐<br> bottomRight：底部居右对齐|
|decoration|(见代码)|

```dart
decoration: BoxDecoration(
  color: Colors.blue,
  border: Border.all(
  color: Colors.red,
    width: 2.0,
  ),
  borderRadius:
  BorderRadius.all(
    Radius.circular(8.0)
  )
)
```
|参数|说明|
|  ----  | ----  |
|margin|-|
|padding|EdgeInsets类|
|transform|-|
|height|-|
|width|-|
|child|-|

* Image.asset() 本地图片
* Image.network() 远程图片

|参数|说明|
|  ----  | ----  |
|alignment|同上|
|color / colorBlendMode|(见代码)|
```dart
child: Image.network(
	"http://pic.baike.soso.com/p/20130828/20130828161137-1346445960.jpg",
	alignment: Alignment.topLeft,
	color: Colors.red,
	colorBlendMode:
	BlendMode.colorDodge, 
	repeat: ImageRepeat.repeatX,
	fit: BoxFit.cover,
), 
```
|参数|说明|
|  ----  | ----  |
|fit|BoxFit.fill:全图显示，图片会被拉伸，并充满父容器。<br>BoxFit.contain:全图显示，显示原比例，可能会有空隙。<br>BoxFit.cover：显示可能拉伸，可能裁切，充满（图片要充满整个容器，还不变形）<br>BoxFit.fitWidth：宽度充满（横向充满），显示可能拉伸，可能裁切。<br>BoxFit.fitHeight ：高度充满（竖向充满）,显示可能拉伸，可能裁切。<br>BoxFit.scaleDown：效果和 contain 差不多，但是此属性不允许显示超过源图片大小，可小不可大。|
|height|-|
|width|-|
|repeat|ImageRepeat.repeat : 横向和纵向都进行重复，直到铺满整个画布。<br>ImageRepeat.repeatX: 横向重复，纵向不重复。<br>ImageRepeat.repeatY：纵向重复，横向不重复。|


* ListView()

|参数|说明|
|  ----  | ----  |
|scrollDirection|Axis.horizontal 水平列表 <br> Axis.vertical 垂直列表|
|padding|-|
|resolve|组件反向排序|
|children|List<Widget>|
	
```dart
// 静态列表
return Center(
	child: ListView(
		children: <Widget>[
			ListTile(
				leading: Icon(Icons.phone), // 前缀图标
				title: Text("this is list",style: TextStyle(fontSize: 28.0),),
				subtitle: Text('this is list this is list'),
				),
			ListTile(
				title: Text("this is list"),
				subtitle: Text('this is list this is list'),
				trailing: Icon(Icons.phone),  // 后缀图标
				)
...
		]
	)
```

// 动态列表
```dart
class HomeContent extends StatelessWidget{
   List<Widget>  _listViewData(){
    List<Widget> list = List();
    for (var i = 0; i <  20; i++) {
      list.add(
        ListTile(
        title: Text('我是第$i个cell'),
      ));
    }
  return list;
  }
  @override
  Widget build(BuildContext context) {
    return ListView(
      padding: EdgeInsets.all(10),
      scrollDirection: Axis.vertical,
      children: this._listViewData(),
    );
  }

}
```

* GridView.count()
* GridView.builder()

|参数|说明|
|  ----  | ----  |
|scrollDirection| Axis| 滚动方法|
|padding| EdgeInsetsGeometry类| 内边距|
|resolve| bool| 组件反向排序|
|crossAxisSpacing| double| 水平子 Widget 之间间距|
|mainAxisSpacing| double| 垂直子 Widget 之间间距|
|crossAxisCount| int| 一行的 Widget 数量|
|childAspectRatio |double |子Widget 宽高比例|
|children |<Widget>[ ]|
|gridDelegate| SliverGridDelegateWithFixed <br>CrossAxisCount（常用）<br> SliverGridDelegateWithMax<br> CrossAxisExtent| 控制布局主要用在GridView.builder 里面
	
```dart
// 写法一
GridView.count(
	//水平子Widget之间间距
	crossAxisSpacing: 10.0,
	//垂直子Widget之间间距
	mainAxisSpacing: 30.0,
	//GridView内边距
	padding: EdgeInsets.all(10.0),
	//一行的Widget数量
	crossAxisCount: 2,
	//子Widget宽高比例
	childAspectRatio: 2.0,
	//子Widget列表
	children: getWidgetList(),
);

// 写法二
Padding(
      padding: const EdgeInsets.all(10),
      child: GridView.builder(
        primary: false,
        gridDelegate:
            SliverGridDelegateWithFixedCrossAxisCount(crossAxisCount: 2),
        scrollDirection: Axis.horizontal,
        children: ...
      )
)

// 更多用法
https://book.flutterchina.club/chapter6/gridview.html
```

* 布局 
  举例Appbar
  
* 路由跳转

* 静态资源配置

* http

* 打包


## 总结

1.使用上手更简单，多端开发效率更高<br>
2.对交互有一定要求<br>
3.插件生态维护与前端类似<br>
4.未来有一定市场<br>
