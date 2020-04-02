## 添加SDK
  下载的AdViewBidSDK_Android-x.x.x.zip
  
  将libs中的库放入到工程中，库明细如下：
  
  |     平台名称    | 对应库名         |   最低版本要求  |
  |----------------|----------------|---------------|
  | AdView         | adview-android-bid-x.x.x.jar |  |
  | 广点通          | gdt_mob_release.jar       | 4.63.993 |
  | 中辉网盟        | WSSDKAds_v1.0.1.aar    | 1.0.1 |  
  | 穿山甲          | open_ad_sdk.aar    | 2.5.2.6 |  
  |      百度      | Baidu_MobAds_SDK.aar    | 5.8 | 
  
  并在gradle中添加依赖:
  
  ```
    defaultConfig {
        ndk { // 根据实际情况添加
            abiFilters 'armeabi-v7a', 'x86', 'arm64-v8a', 'x86_64', 'armeabi'
        }
    }

    packagingOptions {
        doNotStrip "*/armeabi-v7a/*.so"
        doNotStrip "*/x86/*.so"
        doNotStrip "*/arm64-v8a/*.so"
        doNotStrip "*/x86_64/*.so"
        doNotStrip "armeabi.so"
    }

    api 'com.android.support:support-v4:28.0.0'
    api 'pl.droidsonroids.gif:android-gif-drawable:1.2.6'
    api 'com.squareup.okhttp3:okhttp:3.8.0'
    api 'com.squareup.okio:okio:1.13.0'
  ```
  
  注意事项：
  - 将assets目录中的supplierconfig.json添加到项目中的assets目录下，内容无需修改（添加的目的是为了获取OAID，即匿名设备标识，可更好的提升广告填充率）详情参考：msa-alliance.cn；
  - 项目中xml文件下的 bd_file_paths.xml、file_paths.xml、gdt_file_path.xml 复制到您项目中的xml目录下
  - 其他平台的库也可能包含android-query-full.0.26.7.jar或其他版本，请至少保留一个版本。
  - 添加以上sdk，可更好的提供广告填充； ADVIEW平台会为您配置相应的key和广告位。
  - 开屏、视频展示时应尽量全屏展示，否则开屏展示会有展示不完整的情况。针对华为、小米等刘海屏机器，建议参考各厂家对于刘海的适配处理。


## 增加权限和声明代码

```xml
    <!--AdView SDK mandatory or important permissions --> 
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.REQUEST_INSTALL_PACKAGES"/>

    <activity android:name="com.kyview.AdViewVideoActivity"
    android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
    android:hardwareAccelerated="true"/>

    <service android:name="com.kyview.DownloadService" />

    <activity android:name="com.kyview.AdViewLandingPage" />

    <activity android:name="com.kyview.AdActivity" />

```
## 全局设置

  建议请求广告之前要进行初始化
  
  ```js
    InitSDKManager.getInstance().init(applicationContext);
  ```
  
  下载类广告默认弹出二次确认框，如需关闭提示请设置如下；设置后对全部广告生效（具体使用请参考广告条代码集成方式）
   ```js
    InitSDKManager.setDownloadNotificationEnable(false);
   ```
   
  使用AdManager初始化各广告类型
  ```js
    //初始化横幅广告
    BannerManager bannerManager= AdManager.createBannerAd();
    //初始化插屏广告
    InstlManager instlManager= AdManager.createInstlAd();
    //初始化开屏广告
    SpreadManager spreadManager= AdManager.createSpreadAd();
    //初始化原生
    NativeManager nativeManager= AdManager.createNativeAd();
    //初始化视频广告r
    VideoManager videoManager= AdManager.createVideoAd();
  ```

