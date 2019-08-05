
## 可能是 唯一一家提供 图层架构的SDK, 视频编辑, 一层 一层的处理.

*  蓝松短视频编辑SDK, 专业版 android端演示工程.  
*  每个图层都支持移动 缩放 旋转 滤镜,亮暗,隐藏,等属性; 您可以任意个性化. 比如常见的美颜, 滤镜,文字,涂鸦,MV,增加各种动画, 抖音效果等
*  支持AE模板,你可以直接把设计师做好的视频动画工程,输入到我们SDK中,从而直接实现各种个性化的视频效果.使用Ae模板的客户有:微商水印相机,熊猫动态壁纸,小柿饼等

## 版本是3.6.0
- 重写Ae预览合成类, 命名为AECompositionView, 预览后的合成速度提升300%.
- 重新DrawPadAllExecute, 命名为DrawPadAllExecute2,支持视频预裁剪和缩放;
- 视频播放增加变声功能, 音频图层增加变声功能.
- 移动VideoPlayer 到内部jar中,并修改各种回调为OnLSOPlayer [API有变动]
- 优化其他代码.


[更多版本日志](https://github.com/LanSoSdk/LanSoEditor_advance/blob/master/%E7%89%88%E6%9C%AC%E8%AF%B4%E6%98%8E.md)

## 架构介绍
![架构示意图](https://github.com/LanSoSdk/LanSoEditor_advance/blob/master/SDK%E6%9E%B6%E6%9E%84%E5%9B%BE%E7%89%87.png)
### 架构一：AE模板
*   AE模板:  是指设计师用Adobe After Effect做好各种视频动画，比如炫酷视频，文艺/搞笑的场景，相册效果等，根据我们的指导文件导出。蓝松SDK会解析导出的文件,自动还原成AE设计时的动画效果, 无需开发者再一帧一帧的绘制, 开发者只需要做的是：引导用户选择素材，然后替换即可,执行后，即可得到用户自己的效果。
*   APP可参考：小柿饼， 微商水印相机, 熊猫动态壁纸, 壁纸多多等

### 架构二： 图层和容器.  
*   图层是所有素材的集合, 容器是处理的线程; 所有的画面分成一层一层的来处。
*   容器：用来处理各种素材的线程，分为 [容器前台线程] 和 [容器后台线程]。
*   图层： 所有素材的载体。对视频编辑，则把向容器里增加一个视频层；想在上面放图片，就再放一个图片图层； 想放效果视频，则放一个mv层；想增加滤镜则每个图层都支持滤镜实时切换。
*   和UI布局的对比： UI布局是这样的：先增加一个layout，然后放按钮、文本、图片等；则我们SDK则是：先设置DrawPad，然后放视频层，图片层，文字层等；
*   视频图层，可引出多个子图层； 子图层是克隆当前画面， 从而实现同一个画面分裂出多个相同的画面,比如灵魂出窍,模糊背景, 错位等抖音的效果;

### 当前具有的图层种类有(11种): 
*  一下图层均继承父类 Layer.java ; Layer.java支持 移动 缩放 旋转 滤镜,亮暗,隐藏,区域隐藏等功能.
*  视频图层     VideoLayer
*  摄像头图层   CameraLayer
*  图片图层     BitmapLayer
*  MV图层       MVLayer
*  UI图层       ViewLayer
*  Canvas图层   CanvasLayer
*  Data图层     DataLayer
*  Gif图层      GifLayer
*  YUV图层      YUVLayer
*  双视频图层   TwoVideoLayer
*  纹理图层     TextureLayer
*  子图层   SubLayer   (视频图层和摄像头图层支持子图层, 比如抖音的 灵魂出窍,则可以用子图层实现;)
*  注1：可多种图层混合叠加，也可以同时增加多个相同类型的图层。 如VideoLayer+BitmapLayer+ViewLayer或多个BitmapLayer叠加。
*  注2：可关于每个图层的功能,可联系我们,索取更多技术文档.
			

## 更仅一步说:
*	1， 您想给视频增加滤镜，则可以在开启Drawpad后,增加一个视频图层,并给图层设置滤镜效果即可. 也可以设置压缩,缩放或其他功能.
* 2,  您想给视频增加图片,文字. 则可以用 视频图层+Canvas图层+ bitmap图层,三个叠加一起,即可完成.当然也可以在指定位置,指定时间增加,也可以增加后旋转移动缩放等操作.
* 3, 您想把多种图层合成视频. 则可以 增加多个 [图片图层], 可以设置图片的各种飞入飞出,旋转,移动等效果.
* 4，你用 【UI图层  ViewLayer或CanvasLayer】在容器上作画， 就是把精美的UI界面转换为视频， 当然我们的设计，也可以后台处理。
* 5， 你用  【视频图层】 + 【MV图层】 在容器上作画， 就是在视频中叠加MV的效果。
* 6， 你用  【视频图层】 + 【Gif图层】 在容器上作画， 就是在视频中叠加Gif动画的效果。
* 7， 我们针对每个图层都做了举例，您可以在我们Demo中找到；
* 8， 可以在前台工作， 也可以在后台处理。
* 9， 此SDK采用为收费授权,公司性质的合作,为了您项目更好的进行,欢迎和我们联系.谢谢!


## 下载地址: 
*  https://github.com/LanSoSdk/LanSoEditor_advance

## 我们有基本视频编辑,以方便您项目中基本需求：
*	https://github.com/LanSoSdk/LanSoEditor_common

## 我们的IOS版本， 欢迎您的使用：
*	https://github.com/LanSoSdk/LanSongEditor_IOS

## 联系方式:
*   QQ 1852600324 
*   Email:support@lansongtech.com
*   网址: www.lansongtech.com
*  如果您下载过慢, 可联系我们, 索取最新的工程包 或向我们索取演示APK安装包.

## 使用案例
*   我们从事的是：商业SDK开发、更新和维护；
*   当前包括500强 大公司在内的大约300+多个上线APP在使用，行业涉及 社交、微商、广场舞、直播、工具、母婴、舞蹈、厨艺、金融、炫酷等多种行业
*   欢迎联系我们，索取相关案例信息和授权说明
