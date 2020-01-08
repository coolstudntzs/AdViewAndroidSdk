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
  
  并添加依赖:
  
  ```
    api 'com.android.support:support-v4:28.0.0'
    api 'pl.droidsonroids.gif:android-gif-drawable:1.2.6'
    api 'com.squareup.okhttp3:okhttp:3.8.0'
    api 'com.squareup.okio:okio:1.13.0'
  ```
  
  注意事项：
  -将assets目录中的supplierconfig.json添加到项目中的assets目录下，并且将文件中对应平台的appid替换成您的（添加这个的目的是为了获取OAID，即匿名设备标识，可以更好的提升广告填充率）。
  
  -项目中xml文件下的 bd_file_paths.xml、file_paths.xml、gdt_file_path.xml 复制到您项目中的xml目录下。
  
  -竞价sdk增加了以上sdk，是为了更好地广告填充，我们增加了多渠道广告填充功能；这些渠道广告收入由ADVIEW代结，ADVIEW平台会为您配置相应的key和广告位。
  
  -开屏、视频展示时应尽量全屏展示，否则开屏展示会有展示不完整的情况。针对华为、小米等刘海屏机器，建议参考各厂家对于刘海的适配处理。

## 增加权限和声明代码

```xml
  <!--AdView SDK mandatory or important permissions，用户需要添加的 -->
  <uses-permission android:name="android.permission.INTERNET" />
  <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
  <uses-permission android:name="android.permission.READ_PHONE_STATE" />
  <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
  <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
  <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
  <uses-permission android:name="android.permission.REQUEST_INSTALL_PACKAGES"/>
  注：8.0以上必须加REQUEST_INSTALL_PACKAGES权限，否则安装不上

  <!— 必须添加如下代码，否则将导致点击无效-- >
  <activity
        android:name="com.kyview.AdViewVideoActivity"
        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
        android:hardwareAccelerated="true" >
  </activity> 
  <service android:name="com.kyview.DownloadService" />
  <activity android:name="com.kyview.AdViewLandingPage" />
  <activity android:name="com.kyview.AdActivity" />

  <provider
        android:name="com.bytedance.sdk.openadsdk.multipro.TTMultiProvider"
        android:authorities="${applicationId}.TTMultiProvider"
        android:exported="false" />

  <provider
       android:name="com.bytedance.sdk.openadsdk.TTFileProvider"
       android:authorities="${applicationId}.TTFileProvider"
       android:exported="false"
       android:grantUriPermissions="true">
       <meta-data
           android:name="android.support.FILE_PROVIDER_PATHS"
           android:resource="@xml/file_paths" />
  </provider>

  <activity
      android:name="com.baidu.mobads.AppActivity"
      android:configChanges="keyboard|keyboardHidden|orientation"
      android:theme="@android:style/Theme.Translucent.NoTitleBar" />
  <provider
      android:name="com.baidu.mobads.openad.FileProvider"
      android:authorities="${packageName}.bd.provider"
      android:exported="false"
      android:grantUriPermissions="true">
      <meta-data
           android:name="android.support.FILE_PROVIDER_PATHS"
           android:resource="@xml/bd_file_paths" />
  </provider>
```
## 全局设置

  建议请求广告之前要进行初始化
  
  ```java
    InitSDKManager.getInstance().init(context, appId);
  ```
  
  下载类广告默认弹出二次确认框，如需关闭提示请设置如下；设置后对全部广告生效（具体使用请参考广告条代码集成方式）
   ```java
    InitSDKManager.setDownloadNotificationEnable(false);
   ```
