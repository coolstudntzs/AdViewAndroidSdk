## 代码混淆
  
  如需使用proguard混淆代码，需确保不要混淆SDK的代码和support-v4和support-v7。请在proguard.cfg文件（或其他混淆文件）尾部添加如下配置：
  
  ```
    -dontwarn
    -keep public class com.kyview.** {*;} 
    -keepclassmembers class * {public *;}
    -keep public class  com.kuaiyou.** {*;}
    -keep public class  com.baidu.** {*;}
    -keep class com.qq.e.** {
       public protected *; 
    }
    -keep class android.support.v4.**{
       public *;
    }
    -keep class android.support.v7.**{
        public *;
    }
    -keep class com.bun.miitmdid.core.** {*;}
    -keep class com.androidquery.callback.** {*;}
    -keep class com.bun.miitmdid.core.** {*;} 
    -keep class com.bytedance.sdk.openadsdk.** { *; }
    -keep public interface com.bytedance.sdk.openadsdk.downloadnew.** {*;}
    -keep class com.ss.sys.ces.* {*;}
    -keep class com.my.sxg.** { *; }
    -keep class com.xm.** { *; }
    -optimizationpasses 5
    -dontusemixedcaseclassnames
    -dontskipnonpubliclibraryclasses
    -dontpreverify
    -verbose

  ```
  目前Adview SDK混淆支持proguard4.6以上的版本，开发者可以去[proguard](http://sourceforge.net/projects/proguard/files/proguard/)官方网站下载4.6或以上版本；
