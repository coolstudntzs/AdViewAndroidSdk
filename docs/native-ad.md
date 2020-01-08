## 简介

## 接入代码示例
```js
  //初始化原生广告（传入的参数依次为 Context，sdkKey,广告位id,监听接口）
  AdViewNativeManager  adViewNative = new AdViewNativeManager (this, appId, posId, nativeAdCallBcak);
  //请求广告 （可选参数 ：广告条数）
  adViewNative.requestAd();
  //头条广告打底，需要设置广告尺寸
  adViewNative.setAdSize(1080,400);
  nativeBean = (HashMap) nativeAdList.get(0);
  // 汇报展示
  adViewNative.reportImpression((String) nativeBean.get("adId"));
  // 点击汇报 传入的参数为当前广告的id -->对应map的adId字段，点击广告View的坐标，坐标相对广告位左上角为原点
  adViewNative.reportClick((String) nativeBean.get("adId"), 
  (int)event.getX(),(int)event.getY());
  //对于原生视频广告，需要添加如下汇报方法
  //视频开始播放时上报
  adViewNative.reportVideoStatus(this,(String) nativeAd.get("adId"),1); 
  //视频播放1/2时上报
  adViewNative.reportVideoStatus(this,(String) nativeAd.get("adId"),2); 
  //视频播放完成时上报
  adViewNative.reportVideoStatus(this,(String) nativeAd.get("adId"),3);
```

## 回调接口说明

```js
  public interface AdViewNativeListener {
      /**
      * 当广告请求成功时调用该函数. 
      */
      public void onNativeAdReceived(List<HashMap> nativeAdList);
      /**
      * 当广告请求失败时调用该函数.
      */
      public void onNativeAdReceiveFailed(String errorCode);
      /**
      * 下载进度状态码.
      */
      public void onDownloadStatusChange(int arg0);
  }
```
## 原生字段说明

  - 原生通用字段（任何广告类型均返回）

 |     字段     | 类型         |     描述       |
 |-------------|--------------|---------------|
 |adId	        |String       |	广告Id，用于区分广告内容|
 |title	        |String       |  	广告标题      |
 |description   |	String      |	广告描述内容    |



  - 原生图文广告
  
  |     字段     | 类型         |     描述       |
  |-------------|--------------|---------------|
  | adIcon      | String       | Icon图片链接   |
  |adImage      |	String	     |大图数据的图片链接|
  |adFlagLogo   |	String       |	Logo         |
  |adFlagIcon	  |String        |	Icon         |
  |sec_description|String	     |补充广告描述文本  |
  |imageList    |	List	       |原生图片数组（返回多个图片） |
  |nativeView	  |View	         |已渲染的原生View（可选） |
  |imageWidth   |	int          |	大图宽         |
  |imageHeight  |	int          |	大图高         |
  |iconWidth    |	int          |	Icon宽         | 
  |iconHeight   |	int	         |Icon高       |

  - 原生视频广告

  |     字段     | 类型         |     描述       |
  |-------------|--------------|---------------|
  |videoUrl	|String	       |视频物料下载地址      |
  |iconUrl	|String	       |视频icon图片地址      |
  |duration	|String	       |视频播放时长          |
  |preImage	|String	       |视频前贴片图片地址     |
  |endHtml	|String	       |播放完整页面html      |
  |endImgUrl	|String	     |播放完成页面图片地址    |



