
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
## 横幅尺寸说明

  |     字段     |        描述        |
  |-------------|-------------------|
  |AdManager.BANNER_SMART	|根据广告尺寸智能分配比例（推荐）     |
  |AdManager.BANNER_AUTO_FILL	|宽度优先，横向充满               |
  |AdManager.BANNER_480X75	|按照480*75 dp的比例充满          |
  |AdManager.BANNER_728X90	|按照728*90 dp的比例充满     |


