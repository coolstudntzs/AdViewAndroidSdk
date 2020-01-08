## 简介


## 接入代码示例

```js
  //初始化视频广告(传入参数依次为Context、sdkKey、广告位id、监听接口、是否贴片）
	AdViewVideoManager videoManager = new AdViewVideoManager(this, appId, posId, adViewVideoInterface, false);
	//当视频回调onVideoReady接口调用时，表示视频加载完毕 可以播放
	videoManager.playVideo(context);
  //设置视频播放时的背景颜色
  videoManager.setVideoBackgroundColor(“#000000”);
  //设置视频播放视频的横竖屏方向
	videoManager.setVideoOrientation(0);
  //获取当前视频状态，判断是否准备完毕
	videoManager.isReady();
```

## 回调接口说明
  
  ```js
  public interface AdViewVideoListener {   
	 /**
    * 当广告请求成功时调用该函数. 
    */
    public void onReceivedVideo(String vast);
    /**
    * 当广告请求失败时调用该函数.
    */
    public void onFailedReceivedVideo(String errorCode);
    /**
	  * 视频广告准备完毕时调用，在此之后可以进行视频展示
	  */
	  public void onVideoReady();
    /**
	  * 视频广告开始播放时调用
	  */
	  public void onVideoStartPlayed();
	  /**
	  * 视频广告播放结束时调用
	  */
	  public void onVideoFinished();
	  /**
	  * 视频广告被关闭时调用，如需要再次缓存视频广告，请在此接口调用后再次请求广告
	  */
	  public void onVideoClosed();
	  /**
	  * 视频广告播放错误时调用
	  */
	  public void onPlayedError(String error);
}

  ```
