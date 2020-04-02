## 简介

  开屏广告以App启动作为曝光时机，提供5s的可感知广告展示。用户可以点击广告跳转到目标页面；或者点击右上角的“跳过”按钮，跳转到app内容首页

## 接入代码示例

 ```js
	//初始化Instl（传入的参数依次为 Context，appId, posId，需要展示开屏广告的外层布局）
	spreadManager.loadSpreadAd (context, APPID, POSID, parentView);
	
	//设置顶部倒计时通知方式
	spreadManager.setSpreadNotifyType(AdManager.NOTIFY_COUNTER_NULL);
	
	// 设置开屏广告背景颜色
	spreadManager.setBackgroundColor (“#000000”);
	
	//设置开屏广告监听回调
	spreadManager.setSpreadListener (this);
```
## 回调接口说明

```js
    public interface AdViewSpreadListener{
    
		//当广告点击时调用该函数. 
		void onAdClicked();
	
		//当广告展示时调用该函数. 
		void onAdDisplayed();
	
		//当收到广告时调用该函数. 
		void onAdReceived();
	
		//当广告请求失败时调用该函数. 
		void onAdFailedReceived(String error);
	
		//当广告关闭时调用该函数. 
		void onAdClosed();
	
		//展示时间结束将要关闭时调用该函数. 
		void onAdSpreadPrepareClosed();
	}
```
## 开屏顶部通知设置
  
  |     枚举名称   | 描述    |  
  |----------------|----------------|
  | NOTIFY_COUNTER_NULL        | 不显示任何倒计时提示 | 
  | NOTIFY_COUNTER_NUM         | 设置后顶部显示倒计时       | 
  | NOTIFY_COUNTER_TEXT        | 设置后顶部显示为跳过按钮（在规定展示时间之后才会出现）    |
  
  ## 其他
  - 针对api>19的机型，建议显示开屏时隐藏NavigationBar，代码如下：
  ```javascript
	if(Build.VERSION.SDK_INT >= 19) {
		View decorView = getWindow().getDecorView();
		int uiOptions = View.SYSTEM_UI_FLAG_HIDE_NAVIGATION
            | View.SYSTEM_UI_FLAG_IMMERSIVE_STICKY;
		decorView.setSystemUiVisibility(uiOptions);
	}
  ```

