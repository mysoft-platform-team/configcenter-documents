# 明源云配置中心开放文档

## 客户端配置

1. 引用Mysoft.Config.Client.DLL
2. 初次调用前应执行配置中心客户端的初始化：Mysoft.Config.Client.ConfigManager.Init()
3. 配置当前站点的默认环境标识和默认站点标识：
```xml
<!--配置中心：环境标识-->
<add key="configcenter-environmentid" value="product"/>
<!--配置中心：站点标识-->
<add key="configcenter-appid" value="erp"/>
```

## 客户端调用接口

1. 配置中心客户端初始化
···csharp
/// <summary>
/// 执行客户端初始化动作（使用传入的参数）
/// </summary>
/// <param name="serviceUri">配置中心URI</param>
/// <param name="envKey">环境标识</param>
/// <param name="appId">站点标识</param>
public static void Init(string serviceUri, string envKey, string appId);

/// <summary>
/// 执行客户端初始化动作（使用配置的值）
/// </summary>
public static void Init();
···

1. 按环境标识和站点标识读取全部配置

2. 按