## 播放器API
最新版本：2.5.3

## 更新历史
[查看更新历史链接](https://github.com/ejups/epsH5Player/releases)

### 播放器初始化参数
| 参数 |	值类型	| 说明|	默认值|	是否必填|
| :---: | :---: | :--- | :---: | :---: |
| width |	Number | 播放器宽度，单位是px	|H5播放器是屏幕宽度，flash播放器是840px |	否 |
| height |	Number |	播放器高度，单位是px|	H5播放器是屏幕宽度的9/16，flash播放器是480px |	否 |
| wrapElemId |	String|	父容器ID，包裹播放器的DOM标签ID名称	| 无|	是 |
| com |	String|	项目组名称缩写	| 无|	是 |
| type | Number| 	调用类型：0为自适应移动端或PC端，1为调用H5播放器，2为调用flash播放器| 	无	| 是|
| liveId| 	String| 	直播ID| 	无| 	是|
| videoType| 	Number| 	调用类型：1为直播，2为点播	 |无 |	是 |
| videoUrl| 	String或者Array| 	各个模式中都可用String；在移动端点播可使用Array型，代表两个视频，后一个为备用视频地址| 	无|	是 |
| imageUrl| 	String| 	播放器的预览图片地址| 	无| 	是|
| auto	| Boolean| 	调用类型：true为自动播放，false不自动播放（部分手机不支持自动播放）| 	false| 	是|
| xmlid| 	String| 	Flash播放器调用远程的调用接口（Flash播放器专用）| 	无| 	否|
| detailHref| 	String| 	详情链接（h5播放器专用）| 	无| 	否|
| volume| 	number| 	控制起始音量（移动端不支持）| 	50| 	否|
| fullscreenStart| 	方法| 	点击进入全屏回调函数（H5播放器专用）| 	无| 	否|
| fullscreenEnd| 	方法| 	点击退出全屏回调函数（H5播放器专用）| 	无| 	否|
| playStart | 	方法| 	视频开始播放回调函数| 	无| 	否|
| playCompelete | 	方法| 	视频结束播放回调函数 | 	无| 	否|

### 播放器回调方法
| 参数 |	类型	| 说明|	返回值|	用法|
| :---: | :---: | :--- | :---: | :---: |
| turnOn |	方法 | ios开启弹幕	|无 |	_ejuInit.turnOn() |
| turnOdd |	方法 | ios关闭弹幕	|无 |	_ejuInit.turnOff() |
| messageAdd |	方法 | ios发送弹幕	|无 |	_ejuInit.messageAdd() |
| isCommentsOn |	方法 | ios返回弹幕是否开启	|布尔值 |	_ejuInit.isCommentsOn() |
| reload |	方法 | H5切换视频方法(H5播放器专用)	|无 |	_ejuInit.reload() |
| fPlay |	方法 | 播放器视频播放方法	|无 |	_ejuInit.fPlay() |
| fPause |	方法 | 播放器视频暂停方法	|无 |	_ejuInit.fPause() |
| getCurrentTime |	方法 | 播放器获取当前视频时间方法	| number |	_ejuInit.getCurrentTime() |
| getVideoTime |	方法 | 播放器获取当前视频总时长（点击播放后才生效，h5不支持m3u8格式的点播文件）	| number |	_ejuInit.getVideoTime() |

### 播放器快速上手
<pre><code className="javascript">
var _ejuInit = _ejuInit || {};       //创建初始化实例
    _ejuInit.width = "400";          //选填，播放器宽度，flash播放器默认宽度840px，h5播放器默认宽度为屏幕宽度
    _ejuInit.height = "300";         //选填，播放器高度，flash播放器默认高度480px，h5播放器默认高度为屏幕宽度的9/16
    _ejuInit.wrapElemId = "ejuPlayerWrap";   //父容器id
    _ejuInit.type = 0;                   //必填，调用播放器类型，0为自适应移动端或PC端，1为调用h5播放器，2为调用flash播放器
    _ejuInit.com = 'leju_xf';            //必填，项目组名称缩写
    _ejuInit.videoQueue = [              //必填，视频相关设置
          {
             liveId: "21093",             //必填
             videoType: 2,                //必填，1为直播，2为点播
             videoUrl: "rtmp://pili-live-rtmp.qdtong.net/leju-live-2/5507bd",   //必填，播放地址
             imageUrl: "http://ww2.sinaimg.cn/orj480/8191f1c3gw1f6hoegba6xj23402c0hdu.jpg",   //必填，预览图
             auto: true,                   //选填，自动播放
             volume: 20                   //音量
           }
        ];
    _ejuInit.playCompelete = function () {           //选填，视频结束回调函数
      console.log('done');
    };
    _ejuInit.playStart = function () {               //选填，视频开始回调函数
      console.log('start');
    };
    /*插入脚本文件*/
 (function () {
    var _ejuScript = document['createElement']('script');
        _ejuScript.type = 'text/javascript';
        _ejuScript.async = true;
        _ejuScript.src = '//static-live.ejudata.com/eju_video/2.5.3/init.js';     //支持http和https访问的加载文件地址
    var _ejuSrc = document.getElementsByTagName('script')[0];
        _ejuSrc.parentNode.insertBefore(_ejuScript, _ejuSrc)
 })();
</code></pre>
