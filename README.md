## 开发准备

### SDK 获取


### SDK 配置

直接下载github上提供的源代码，使用SDK之前，加载dist目录里的cos-js-sdk-v4.js文件即可。

```javascript
<script type="text/javascript" src="cos-js-sdk-v4.js"></script>

```

###初始化

```js

	//初始化逻辑
	//特别注意: JS-SDK使用之前请先到console.qcloud.com/cos 对相应的Bucket进行跨域设置
	var cos = new CosCloud({
		appid: appid,// APPID 必填参数
		bucket: bucket,//bucketName 必填参数
		region: 'sh',//地域信息 必填参数 华南地区填gz 华东填sh 华北填tj
		getAppSign: function (callback) {//获取签名 必填参数

			//下面简单讲一下获取签名的几种办法

			//1.搭建一个鉴权服务器，自己构造请求参数获取签名，推荐实际线上业务使用，优点是安全性好，不会暴露自己的私钥
			//拿到签名之后记得调用callback
			/**
			 $.ajax('SIGN_URL').done(function (data) {
				var sig = data.sign;
				callback(sig);
			});
			 **/

			//2.直接在浏览器前端计算签名，需要获取自己的accessKey和secretKey, 一般在调试阶段使用
			//拿到签名之后记得调用callback
			//var res = getAuth(); //这个函数自己根据签名算法实现
			//callback(res);


			//3.直接复用别人算好的签名字符串, 一般在调试阶段使用
			//拿到签名之后记得调用callback
			//callback('YOUR_SIGN_STR')
			//

		},
		getAppSignOnce: function (callback) {//单次签名，必填参数，参考上面的注释即可
			//填上获取单次签名的逻辑
		}
	});


```


