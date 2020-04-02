
## 简介
Banner广告(横幅广告)位于app顶部、中部、底部任意一处，横向贯穿整个app页面；当用户与app互动时，Banner广告会停留在屏幕上，并可在一段时间后自动刷新

## 接入代码示例
```javascript
  //创建横幅广告（传入的参数依次为 context，appId, posId，尺寸）
  bannerManager.loadBannerAd(activity, APPID, POSID, AdManager.BANNER_SMART);
  
  //设置banner的关闭按钮
  bannerManager.setShowCloseBtn(true);
  
  //设置广告切换时间(秒)，如果不设置默认不自动切换广告
  bannerManager.setRefreshTime(15);
  
  //设置监听回调
  bannerManager.setBannerListener (this);
```
## 回调接口说明
```javascript
  public interface AdViewBannerListener{
  
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
    
	  //广告渲染成功. 
	  void onRenderSuccess();
}

```

