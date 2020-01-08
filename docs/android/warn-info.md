## 注意事项
  - Android Q 适配
  
    Android Q中禁止IMEI的获取，本SDK中使用 miit_mdid_x.x.x.aar 来获取移动设备匿名广告ID，如设备同时无法获取IMEI和匿名广告ID，将会影响广告收益！
    
      使用方法：
  
      - 把 miit_mdid_x.x.x.aar 拷贝到项的 libs 目录，并设置依赖，其中 x.x.x 代表版本号。
      
      - 将 supplierconfig.json 拷贝到项目 assets 目录下，需要设置 appid 的部分需要去对应厂商的应用商店里注册自己的 app。（仅需要修改vivo的appId）
      - 设置依赖 implementation files(‘libs/miit_mdid_x.x.x.aar’)
      
