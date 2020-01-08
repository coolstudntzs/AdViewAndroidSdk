
## 简介
开屏广告以App启动作为曝光时机，提供5s的可感知广告展示。用户可以点击广告跳转到目标页面；或者点击右上角的“跳过”按钮，跳转到app内容首页

## 接入代码示例
```java
  //初始化banner（传入的参数依次为 context，sdkKey，尺寸，是否刷新）
  AdViewBannerManager adViewBIDView = new AdViewBannerManager (context, sdkKey, adSize, true);
  //设置下载类广告非wifi状态下是否显示二次确认窗口。请在广告初始化后调用该方法
  InitSDKManager.setDownloadNotificationEnable(true);
  //设置banner的关闭按钮
  adViewBIDView.setShowCloseBtn(false);
  //设置广告切换时间(秒)，如果不设置默认不自动切换广告,
  adViewBIDView.setRefreshTime(15);
  //设置广告自动切换时动画效果
  adViewBIDView.setOpenAnim(true);
  //设置监听回调
  adViewBIDView.setOnAdViewListener(this);
  //当不再需要展示广告时，调用以下方法释放资源
  adViewBIDView.destory();
```
## 回调接口说明
```java
  public interface AdViewBannerListener{
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
  }
```

