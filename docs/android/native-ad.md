## 简介

  相比于前文介绍的Banner广告、插屏广告等，原生广告提供了更加灵活、多样化的广告样式选择
  
  原生广告分为两大类：模板和自渲染，模板方式支持开发者自主调整原生模板参数；而自渲染方式更加灵活，提供一个包含广告素材资源的对象，开发者可以自由“拼合”这些素材并且展示它们

## 接入代码示例
```js
    //初始化原生广告（传入的参数依次为 Context，appId, posId ）
    nativeManager.loadNativeAd(this, APPID, POSID);
  
    //请求广告
    nativeManager.requestAd(1);
  
    //设置广告尺寸,单位为dp
    nativeManager.setAdSize(320,150);
  
    //设置广告监听
    nativeManager.setNativeListener(this);
  
    //广告返回ArrayList<NativeAd>时可设置广告交互监听
    nativeAd.setInteractionListener(this)
```

## 原生广告返回接口说明

```js
    public interface AdViewNativeListener {
  
        //当广告请求成功时调用该函数. 
        void onNativeAdReceived(ArrayList<NativeAd> nativeAdList);
      
        //当广告请求失败时调用该函数.
        void onNativeAdReceiveFailed(String errorCode);
    }

```

## 原生广告交互接口说明
```js
    public interface AdNativeInteractionListener {
        //当广告被关闭时调用
        void onAdClosed(View view);
    
        //当广告渲染成功时调用
        void onNativeViewRendered(View view);
    
        //当广告渲染失败时调用
        void onNativeViewRenderFailed(String error);
    
        //当广告被点击时调用
        void onNativeViewClicked(View view);
    
        //当广告展示时调用
        void onNativeViewDisplayed(View view);                                            
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
  
 ## 其他
 
 - 原生物料广告（除nativeView字段外）需要开发者自行组合；
 - 当返回nativeView字段时，将不会返回其他原生物料字段，开发者只需将nativeView添加到界面中进行展示即可；开发者可根据nativeView的返回值判断由哪种方式进行展示。
 - 原生物料类型，需要手动添加汇报方法
 
 ```js
    //普通物料类型点击上报
    nativeAd.reportClick(adView, downX, downY); 
  
    //普通物料类型展示上报
    nativeAd.reportImpression(adView); 
  
    //视频开始播放时上报
    nativeAd.reportVideoStatus(this, AdManager.VIDEO_STATUS_START); 
  
    //视频播放1/2时上报
    nativeAd.reportVideoStatus(this, AdManager.VIDEO_STATUS_MEDIUM); 
  
    //视频播放完成时上报
    nativeAd.reportVideoStatus(this, AdManager.VIDEO_STATUS_END);
 ```

 





