# 明源云配置中心调用文档

## 调用前准备

1. 引用Mysoft.Config.Client.DLL。[下载地址](raw/master/配置中心客户端DLL.zip)
2. 初次调用前应执行配置中心客户端的初始化：Mysoft.Config.Client.ConfigManager.Init()
3. 配置当前站点的默认环境标识和默认站点标识：
```xml
<!--配置中心：环境标识-->
<add key="configcenter-environmentid" value="product"/>
<!--配置中心：站点标识-->
<add key="configcenter-appid" value="erp"/>
```
4. 通过```Mysoft.Config.Client.ConfigManager```对象调用以下API。

## 配置读写相关接口

1. 配置中心客户端初始化
```c#
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
```

2. 按环境标识和站点标识读取全部配置
```c#
/// <summary>
/// 读取指定环境标识、指定站点的配置项
/// 如果无法读取，返回空字符串
/// </summary>
/// <param name="envKey">环境名称</param>
/// <param name="appId">appId</param>
/// <param name="name">配置项名称</param>
/// <returns></returns>
public static string GetSetting(string envKey, string appId, string name);

/// <summary>
/// 获取指定appId的配置项。
/// </summary>
/// <param name="appId">appId</param>
/// <param name="name">配置项名称</param>
/// <returns></returns>
public static string GetSetting(string appId, string name);

/// <summary>
/// 获取当前站点的配置项。
/// </summary>
/// <param name="name">配置项名称</param>
/// <returns></returns>
public static string GetSetting(string name);

```


3. 保存配置项
```c#
/// <summary>
/// 保存配置的值到配置中心
/// </summary>
/// <param name="name">配置名称</param>
/// <param name="value">配置的值</param>
/// <param name="envKey">环境Key，为null时使用当前环境key</param>
/// <param name="appId">应用程序标识，为null时使用当前站点key</param>
public static void SetSetting(string name, string value, string envKey = null, string appId = null) 
```

## 站点相关接口

1. 增加站点
```c#
/// <summary>
/// 向配置服务增加一个站点信息
/// </summary>
/// <param name="envKey">环境标识</param>
/// <param name="siteKey">站点标识</param>
/// <param name="name">站点显示名称</param>
/// <param name="url">站点URL</param>
/// <param name="defineXml">站点配置定义XML</param>
public static void AddSite(string envKey, string siteKey, string name, string url, string defineXml)
```

2. 读取站点列表
```c#
/// <summary>
/// 向配置服务获取站点列表信息
/// </summary>
/// <param name="envKey">环境标识</param>
public static string[] GetSiteList(string envKey)
```

3. 删除一个站点
```c#
/// <summary>
/// 向配置服务删除一个站点
/// </summary>
/// <param name="envKey">环境标识</param>
/// <param name="siteKey">站点标识</param>
public static void DeleteSite(string envKey, string siteKey)
```

4. 读取站点详情
```c#
/// <summary>
/// 读取站点信息
/// </summary>
/// <param name="envKey">环境标识，传入null默认当前环境</param>
/// <param name="siteKey">站点标识</param>
/// <returns></returns>
public static Site GetSiteInfo(string envKey, string siteKey) 

/// <summary>
/// 一个站点
/// </summary>
[Serializable]
public class Site
{
    /// <summary>
    /// 站点Key
    /// </summary>
    [XmlAttribute("key")]
    [JsonProperty("key")]
    public string Key { get; set; }

    /// <summary>
    /// 名称
    /// </summary>
    [XmlAttribute("name")]
    [JsonProperty("name")]
    public string Name { get; set; }

    /// <summary>
    /// 站点地址
    /// </summary>
    [XmlAttribute("url")]
    [JsonProperty("url")]
    public string Url { get; set; }
}
```



## 环境相关接口

1. 增加环境
```c#
/// <summary>
/// 增加环境
/// </summary>
/// <param name="key"></param>
/// <param name="text"></param>
public static void AddEnvironment(string key, string text);
```

2. 读取环境列表
```c#
/// <summary>
/// 读取全部的环境列表
/// key: 环境标识EnvKey
/// value: 显示名称
/// </summary>
/// <returns></returns>
public static List<Service.Models.Environment> GetEnvironmentList()
```

3. 删除一个环境
```c#
/// <summary>
/// 删除环境
/// </summary>
/// <param name="key"></param>
public static void DelEnvironment(string key)
```
