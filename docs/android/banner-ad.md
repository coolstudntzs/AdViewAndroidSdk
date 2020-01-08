
## 简介
Banner广告(横幅广告)位于app顶部、中部、底部任意一处，横向贯穿整个app页面；当用户与app互动时，Banner广告会停留在屏幕上，并可在一段时间后自动刷新

## 接入代码示例
```javascript
  //初始化banner（传入的参数依次为 context，sdkKey，尺寸，是否刷新）
  AdViewBannerManager adViewBIDView = new AdViewBannerManager (context, appId, adSize, true);
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
```javascript
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

