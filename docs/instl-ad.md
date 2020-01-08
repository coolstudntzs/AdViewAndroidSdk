## 简介

  插屏广告是移动广告的一种常见形式，在应用开流程中弹出，当应用展示插页式广告时，用户可以选择点按广告，访问其目标网址，也可以将其关闭，返回应用
  
## 接入代码实例
```javascript
  //初始化Instl（传入的参数依次为 Context，sdkKey，是否可关闭）
  AdViewInstlManager adInstlBIDView=new AdViewInstlManager (context, sdkKey, true);
  //设置监听回调	 
  adInstlBIDView. setOnAdViewListener(this);
```

## 回调接口说明
```javascript
public interface AdViewInstlListener{
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
    void onAdReady();
	  /**
    * 当广告关闭时调用该函数. 
    */
    void onAdClosed();
}
```
