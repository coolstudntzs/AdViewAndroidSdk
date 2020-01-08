## 简介

## 接入代码示例

 ```javascript
  //初始化Instl（传入的参数依次为 Context，sdkKey，需要展示开屏广告的外层布局）
  AdViewSpreadManager  adViewBIDSpread = new AdViewSpreadManager 	(context,sdkKey,parentView);
  //设置顶部倒计时通知方式，默认不通知
  adViewBIDSpread.setSpreadNotifyType(AdViewSpreadManager.NOTIFY_COUNTER_NULL);
  // 设置开屏广告背景颜色
  adViewBIDSpread. setBackgroundColor (backgroundColor);
  //设置开屏广告监听回调
  adViewBIDSpread. setOnAdViewListener (this);
```
## 回调接口说明

```javascript
public interface AdViewSpreadListener{
    /**
    * 当广告点击时调用该函数. 
    */
    void onAdClicked();
	  /**
    * 当广告展示时调用该函数. 
    */
    void onAdDisplayed();
	  /**
    * 当收到广告时调用该函数. 
    */
    void onAdReceived();
	  /**
    * 当广告请求失败时调用该函数. 
    */
    void onAdFailedReceived(String error);
	  /**
    * 当广告关闭时调用该函数. 
    */
    void onAdClosed();
    /**
    * 展示时间结束将要关闭时调用该函数. 
    */
    void onAdSpreadPrepareClosed();
    /**
    * 自定义回调
    */
    void onAdNotifyCustomCallback(int ruleTime,int delayTime);
}
```
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
  - 开屏顶部通知设置
  
  |     枚举名称   | 描述    |   常量   |
  |----------------|----------------|---------------|
  | NOTIFY_COUNTER_NULL        | 不显示任何倒计时提示 | 0  |
  | NOTIFY_COUNTER_NUM         | 设置后顶部显示倒计时       | 1 |
  | NOTIFY_COUNTER_TEXT        | 设置后顶部显示为跳过按钮（在规定展示时间之后才会出现）    | 2 |  
  | NOTIFY_COUNTER_CUSTOM          | 设置后将调用 onAdNotifyCustomCallback()，可在其中自定义通知样式    | 3 |  

