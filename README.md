# tencent_im_plugin

腾讯云IM插件

## Getting Started

## Android 端集成

### 1. 修改 defaultConfig ndk 配置
```
defaultConfig {
    .......
    ndk {
        abiFilters "armeabi-v7a"
    }
}
buildTypes {
    release {
        .......
        ndk {
            abiFilters "armeabi-v7a"
        }
    }
    debug {
        .......
        ndk {
            abiFilters "armeabi", "armeabi-v7a", "arm64-v8a", "x86"
        }
    }
}
```
### 2. 设置混淆规则
```
-keep class com.tencent.** { *; }
```

### 3. 如果启动报错，请修改 AndroidManifest.xml 文件
在 manifest 标签上增加:``xmlns:tools="http://schemas.android.com/tools"``
在 application 标签上增加:``tools:replace="android:label"``

## IOS端集成

## 使用
### 初始化
通过调用 ``TencentImPlugin.init(appid: "xxxxxxx");`` 进行初始化
注意：该方法必须调用且最好仅调用一次，建议在程序启动时调用一次即可。

### 登录
通过调用 ``TencentImPlugin.login(identifier: "用户ID",userSig:"签名，建议通过服务端生成");`` 进行登录
注意：如果已有用户登录，则登录方法会被中断且返回异常!

### 退出登录
如果您需要登出，可以调用：``TencentImPlugin.logout();``

### 获得当前登录用户
``TencentImPlugin.getLoginUser();`` 返回值为当前登录用户ID

### 初始化本地存储
``TencentImPlugin.initStorage(identifier: "用户ID");`` 

### 获得当前登录用户会话列表
``TencentImPlugin.getConversationList();`` 返回值为``List<SessionEntity>``

## 对象实体说明