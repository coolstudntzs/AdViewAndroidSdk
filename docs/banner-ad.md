# 广告条代码创建（单次请求模式）

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
