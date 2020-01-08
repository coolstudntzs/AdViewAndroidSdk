## 添加SDK
  下载的AdViewBidSDK_Android-x.x.x.zip
  
  将libs中的库放入到工程中，库明细如下：
  
  |     平台名称    | 对应库名         |   最低版本要求  |
  |----------------|----------------|---------------|
  | AdView         | adview-android-bid-x.x.x.jar        |  |
  | 广点通          | gdt_mob_release.jar       | 4.63.993 |
  | 中辉网盟        | /index.html    | 1.0.1 |  
  | 穿山甲          | open_ad_sdk.aar    | 2.5.2.6 |  
  |      百度      | Baidu_MobAds_SDK.aar    | 5.8 |  

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
        android:name="com.kyview.AdViewVideoActivity"                            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
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
